---
title: "Javascript helppppp plz (getElementsByClassName method)"
date: 2009-05-18
forum: Programming Talk
---

### Post by Syndacate on 2009-05-18
Hey,

I know some people don't consider javascript programming but since it's development I'd think it goes here anyway.

I am trying to use the getElementsByClass method and it's returning nothing, every time, just an empty array.

Now I'm sorta new to scripting (know Ruby pretty decently) but have been using C/Java, etc. for quite a while, these lines, right here:

```

var links = document.getElementsByClassName("header");
alert(links.length);
alert(links[0]);

```

**I'm running this from a firefox plugin btw**

I ran that on a page that I know (via DOM Tree Inspector) had an element with "header" as the class, the first alert returned "0", the second alert returned "undefined."

I cannot get the getElementsByClass method to work...at all...I even tried the 30 other ones people have written floating around the web that utilize three arguments and two arguments (root, class), etc. and those don't work either.

I can't get the damn method to work and I'm flipping out because of it.  I'm trying to use the one that's defaulted into firefox, it won't work.

HELLLLLLLp :( :( :( (:( x50.

PS:  I also tried single quoting the argument instead of double quoting, that didn't work either :(

---

### Post by iiska on 2009-05-18
Could you post the html markup which you are trying to parse with that script?

---

### Post by myrtle1908 on 2009-05-18
Fairly certain that there isn't a getElementsByClassName (at least when I last checked??).  You can roll your own however.  I use one like this:-

```

<div class="test">Div 1</div>
<div class="test">Div 2</div>

<script language="javascript">
document.getElementsByClassName = function(cls) {
	var found = [];
	var rx = new RegExp('(^| )' + cls + '( |$)');
	var els = this.getElementsByTagName('*');
	for (var i=0; i<els.length; i++) {
		var elClass = els[i].className;
		if (rx.test(elClass)) {
			found.push(els[i]);
		}
	}
	return found;
};

var divs = document.getElementsByClassName('test');
alert(divs.length);
</script>

```

---

### Post by Yacoby on 2009-05-18
> **myrtle1908 said:**
> Fairly certain that there isn't a getElementsByClassName (at least when I last checked??).  You can roll your own however.  I use one like this:-

```

<div class="test">Div 1</div>
<div class="test">Div 2</div>

<script language="javascript">
document.getElementsByClassName = function(cls) {
	var found = [];
	var rx = new RegExp('(^| )' + cls + '( |$)');
	var els = this.getElementsByTagName('*');
	for (var i=0; i<els.length; i++) {
		var elClass = els[i].className;
		if (rx.test(elClass)) {
			found.push(els[i]);
		}
	}
	return found;
};

var divs = document.getElementsByClassName('test');
alert(divs.length);
</script>

```
Why use regex for what IMHO should be a simple string comparison?

Woudln't something like this be faster```

document.getElementsByClassName = function(cls) {
	var found = [];
	var els = this.getElementsByTagName('*');
	for (var i=0; i<els.length; i++) {
		var elClass = els[i].className;
		if (cls == elClass ) {
			found.push(elClass);
		}
	}
	return found;
};
```

---

### Post by iiska on 2009-05-18
> **myrtle1908 said:**
> Fairly certain that there isn't a getElementsByClassName (at least when I last checked??).

Yes there is, but it's Firefox 3 specific function: [https://developer.mozilla.org/en/DOM/document.getElementsByClassName](https://developer.mozilla.org/en/DOM/document.getElementsByClassName)

---

### Post by Yacoby on 2009-05-18
Ah crap. I missed the bit that said you were writing a ff extension.

Try using```

window.content.document
```



```

var links = window.content.document.getElementsByClassName("header");
alert(links.length);
alert(links[0]);
```

---

### Post by myrtle1908 on 2009-05-18
> **Yacoby said:**
> Why use regex for what IMHO should be a simple string comparison?

Woudln't something like this be faster```

document.getElementsByClassName = function(cls) {
	var found = [];
	var els = this.getElementsByTagName('*');
	for (var i=0; i<els.length; i++) {
		var elClass = els[i].className;
		if (cls == elClass ) {
			found.push(elClass);
		}
	}
	return found;
};
```

But it will not find elements who have multiple classes eg. <div class="class1 class2">...</div>

```
<div class="test another">Div 1</div>
<div class="test">Div 2</div>

<script language="javascript">
document.getElementsByClassName = function(cls) {
	var found = [];
	var rx = new RegExp('(^| )' + cls + '( |$)');
	var els = this.getElementsByTagName('*');
	for (var i=0; i<els.length; i++) {
		var elClass = els[i].className;
		if (rx.test(elClass)) {
			found.push(els[i]);
		}
	}
	return found;
};

document.getElementsByClassName2 = function(cls) {
	var found = [];
	var els = this.getElementsByTagName('*');
	for (var i=0; i<els.length; i++) {
		var elClass = els[i].className;
		if (cls == elClass ) {
			found.push(els[i]);
		}
	}
	return found;
};

var divs = document.getElementsByClassName('test');
alert(divs.length);
</script>

```

---

### Post by Syndacate on 2009-05-18
Okay, thank you all for your quick responses.

First off, there is a "getElementsByClassName" in firefox 3.0.* - though I have no objection to using other code.  I've already tried like 10 methods like that (found on the web) but to no avail.

I just used the code you, myrtle (both of them), and the code snippet above - all return 0 elements long, all return undefined for array[0] - that method for some reason just will not work.

I tried it with a regular class name, too, I opened the DOM inspector on my home page and just put in 'header' (first element I found with a class), and it still returned a set of length 0, where a[0] is undefined.

Dammit.

This problem has been messing with me for the last like 4 cumulative hours - and it's simple.

I don't know if anybody has any other suggestions, but I can't paste anymore code - I've commented everything out, what I originally posted IS all the code for that function.  It's like it just doesn't care that it's supposed to work :( :(.

Any more help is greatly appreciated.  Thanks.

PS:  window.content.document.. throws an error

PPS:  I tried all the methods here via the function call in my first post, for elements whos class is right there on the page, all returned an empty array.

Is it possible that "class" in the DOM Inspector ISN'T the same "class name" that the .className method refers to?? (the elements have both attributes of "class" and "classname" as what I'm trying to pull out (both the same)), so it really shouldn't matter...but it's not working so I'm thinking it might.  getElementsByTagName certainly isn't returning null, it's getting lost in translation somewhere..

---

### Post by Yacoby on 2009-05-18
> **Syndacate said:**
> PS:  window.content.document.. throws an error

Try
```
content.document
```

@myrtle1908
Very valid point. I forgot about that :)

---

### Post by Syndacate on 2009-05-18
> **Yacoby said:**
> Try
```
content.document
```

@myrtle1908
Very valid point. I forgot about that :)

That fixed it.

Thank you very much. :D:D

EDIT:
PS:  What the heck happeend to the "thank X person" and "thread closed" tools?

---

