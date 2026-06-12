---
title: "Javascript problem"
date: 2011-03-14
forum: Programming Talk
---

### Post by Peter76 on 2011-03-14
I have the following html:
[HTML]<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Click Test</title>
<meta http-equiv="content-type" content="text/html; charset=UTF-8"/>
<meta http-equiv="content-style-type" content="text/css"/>
<script src="clicktest.js" type="text/javascript"></script>
</head>
<body>
<div id="clicktst">Hello World</div>
</body>
</html>[/HTML]

And the following javscript file:
```
window.onload = function() {
	var maskDiv = document.getElementById( "clicktst" );
	if ( maskDiv ){
		maskDiv.style.cursor = "pointer";	
		maskDiv.onclick = alert( "ok" );
	}
}
```

The problem is that when I open the html in FF,  a popup shows with ok, but when I click on the div nothing happens, though the mouse arrow is correctly set to pointer.
What am I doing wrong here, guess it's something very obvious, but I can't find what.

Thanks, Peter

---

### Post by LoneWolfJack on 2011-03-14
the "onload" event handler is executed as the element is loaded, after than, you need to use a different event handler like onclick.

---

### Post by An Sanct on 2011-03-14
You are using 
[HTML]window.onload[/HTML], which is the function called when <body> is parsed, instead of something like

[HTML]<IMG SRC="button.gif" WIDTH=64 HEIGHT=32  ALT="Button" ONMOUSEDOWN="alert('ok!')">[/HTML]

Take a look here [w3School]("http://www.w3schools.com/js/tryit.asp?filename=tryjs_events")

---

### Post by lykeion on 2011-03-14
I'm not a JavaScript guy (Java coders have a tendency to dislike it) but something like this:
```
window.onload = function() {
	function handleElement(id) {
		if (document.getElementById) {
			var maskDiv = document.getElementById(id);
			maskDiv.style.cursor = "pointer";
			maskDiv.onclick = function() { alert("OK"); }
		}
	}

	handleElement("clicktst");
}
```
Take a look here: [http://www.quirksmode.org/js/contents.html](http://www.quirksmode.org/js/contents.html)

---

### Post by Peter76 on 2011-03-14
@lykeion, thank you so much!; wrapping alert() in an anonymous function did the trick!
DOes anybody know why you have to wrap alert() in a function like this to get it to work, but can call a normal function directly?

Thanks, Peter

---

### Post by myrtle1908 on 2011-03-14
> **Peter76 said:**
> DOes anybody know why you have to wrap alert() in a function like this to get it to work, but can call a normal function directly?

Because the event handler must be a function *reference*, not a function call.

---

### Post by Peter76 on 2011-03-15
> **myrtle1908 said:**
> Because the event handler must be a function *reference*, not a function call.

Thanks for that! I'll do some more reading on that:D

Peter

---

