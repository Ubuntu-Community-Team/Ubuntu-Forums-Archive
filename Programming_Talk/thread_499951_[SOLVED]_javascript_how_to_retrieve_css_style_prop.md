---
title: "[SOLVED] javascript how to retrieve css style property"
date: 2007-07-13
forum: Programming Talk
---

### Post by RocketRanger on 2007-07-13
I know that it's possible to set css style properties using something like:

document.getElementById(id).style.textDecoration = 'underline';

but what can I do if I want to retrieve a property for use elsewhere, like say an anchor's color?

---

### Post by chewearn on 2007-07-13
The style attributes are mostly read and write.  At least, I think most of them are.
So, you can read back what you have assigned, e.g.:

```
 document.getElementById(id).style.textDecoration = 'underline';
alert( document.getElementById(id).style.textDecoration);
document.getElementById(id).style.textDecoration = 'none';
alert( document.getElementById(id).style.textDecoration);

```

The only snag is that, you have to first assign them in javascript.  The default attributes loaded during page refresh from the css file are not readable in javascript.  Therefore, if you originally define the "underline" attribute in css, this statement would give you null:
alert( document.getElementById(id).style.textDecoration);

At least that is the Firefox behaviour; I don't know about other browser.

---

### Post by destructchaos on 2007-07-13
the other browser throws an error and gets pissy.

---

### Post by RocketRanger on 2007-07-13
Yep, that did it. I must say that javascript seems very effective and has been pretty easy to learn, however it does seem to have its own idiosyncracies that you just have to get to grips with.

I'm just glad that there are people who know them and are willing to share :)

---

### Post by RocketRanger on 2007-07-23
There is a way to reference a css element without assigning a value to it first. I bought the Javascript and DHTML cookbook from O'reilly and found that it's possible to do a two step solution to it. 

Appearently Mozilla and the other browser places stylesheets two different places in the DOM and Mozilla references its style object, using css naming convention (background-color) whereas the other one uses Javascript notation (backgroundColor). 

There is a discussion about this in the book which I don't enough about javascript to paraphrase here. Instead I have expanded on an example from the book. 

Idea behind this script is from JavaScript & DHTML Cookbook by Danny Goodman

```
<html>
<head>
	<title>cb_11.12_read_css_values</title>
	<script type="text/javascript" language="javascript1.2">
	
	function getStyleVal (source_id, target_id, IEStyleName, CSSStyleName) {
		var elem = document.getElementById(source_id);
		var target = "";
		
		if (elem.currentStyle) {
			target = currentStyle[IEStyleName];
		} else if (window.getComputedStyle) {
			var compStyle = window.getComputedStyle(elem, "");
			target = compStyle.getPropertyValue(CSSStyleName);
		} else {
			target = "";
		}
		
		document.getElementById(target_id).innerHTML = target;
	}
	
	</script>
	
	<style type="text/css">
	body { background-color:#acaaff; }
	
	</style>
	
</head>

<body id="page_body" onload="getStyleVal('page_body', 'target', 'backgroundColor', 'background-color');
							 getStyleVal('page_body', 'target2', 'marginLeft', 'margin-left')">

<div>Background colour (set via stylesheet):</div>
<div id="target"></div>
<div>Left margin (default value):</div>
<div id="target2"></div>

</body>
</html>


```

---

### Post by chewearn on 2007-07-24
Hey, thanks for the tip.  I never knew about this browser behavior :) I learn all about javascript from various resources on the internet.

The way I workaround this is by avoiding the need to read or write specific styles.  Instead, I define classes in the css; each class encapsulate the styles or attributes I am interested in.

For example, I have a "web" application, which allows me to create/edit multi-level lists.  Here is a sample of the css:

```
div.level0    { padding:10px 1px 1px 1px; font-size:8pt; } 
div.level1    { padding:12px 1px 1px 1px; font-size:14pt; font-weight:bold; } 
div.level2    { padding:8px 1px 1px 20px; font-size:12pt; font-weight:bold; }
```As you can see, I define a class for each level of the list.  The trick here is that I do not need to initialize each html element by javascript, yet I can read back the class attribute, e.g.:

```
if (htmDoc[0].getAttribute("class") == "level1") {
// do something
// note: htmDoc[] is an array of the "div" elements in the html document
}
```Another example, if I need to change a level 1 item to level 2 in the list, I simply change the class, and the document automatically adjust the style:

```
htmDoc[1].setAttribute("class", "level2")
```Also, the advantage from using class (apart from the workaround against initializing specific style) is that I can change the styles in css alone, without the need to search through the javascript codes.  So, if I don't like the bold and want to increase the indent, i simple edit the css, and every get done at once.

---

### Post by RocketRanger on 2007-07-25
That is a very useful tip. Thank you for that. Defining groups in the stylesheet is going to be helpful in keeping a clean design and avoid messy code. Nice.

---

