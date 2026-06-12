---
title: "Simple javascript and html question"
date: 2007-05-14
forum: Programming Talk
---

### Post by tc101 on 2007-05-14
I am trying to write javascript to change the value and font size of the text in a <div>.  
Why doesn't this work?

<html>
	<form name="form1">
		<div name="div1" style="text-align: center; font-size: 48px;">
	 	how do I change text here in a div?
		</div>
		<br>
	</form>
	<input name = "b1" onclick="test1()"  value="javascript test"  type="button">
	<script>
		function test1()
		{
		document.form1.div1.value = "hello";  //why does this give an error
		document.form1.style.fontsize="24px"; //why doesn't this change the fontsize?
		}
	</script>
</html>

---

### Post by Mirrorball on 2007-05-14
A lot of things are wrong. Divs don't have name attributes, they have ids. The way to select a div by its id is:
```
document.getElementById('the-id-you-chose')
```There is no "value" attribute, it's "innerHTML." The font-size attribute is "fontSize," not "fontsize."
```
var div1 = document.getElementById('div1');
div1.innerHTML = 'hello';
div1.style.fontSize = '24px';
```

---

### Post by tc101 on 2007-05-14
Thanks for your help.  You have pointed me in the right direction but there is still some problem.

using

var div1 = document.getElementById('div1');
div1.innerHTML = 'hello';
div1.style.fontSize = '24px';

I still get an error saying "div1 has no properties" when I try to set font size or move data to the innerHTML

I also tried 

var div1 = document.getElementById('form1.div1')

and got the same results.

---

### Post by Mirrorball on 2007-05-14
As I said, the div element needs an id attribute, not a name attribute. Right now it's:
```
<div name="div1" style="text-align: center; font-size: 48px;">
how do I change text here in a div?
</div>
```
But it should be:
```
<div id="div1" style="text-align: center; font-size: 48px;">
how do I change text here in a div?
</div>
```

---

### Post by tc101 on 2007-05-14
Thanks so much Mirrorball.  Now I understand.

---

### Post by tc101 on 2007-05-14
Why is it that sometimes you can do away with the var and sometimes you can't.  

For example this works:

document.getElementById("div1").innerHTML = "changed"

But this does not work:

document.getElementById("div1").style.visibility="hidden"

and needs to be coded this way:

var div1 = document.getElementById("div1");
div1.style.visibility="hidden"

---

### Post by Mirrorball on 2007-05-14
I don't know, I thought it would work either way.

---

### Post by RedSquirrel on 2007-05-15
> **tc101 said:**
> Why is it that sometimes you can do away with the var and sometimes you can't.  

For example this works:

document.getElementById("div1").innerHTML = "changed"

But this does not work:

document.getElementById("div1").style.visibility="hidden"

and needs to be coded this way:

var div1 = document.getElementById("div1");
div1.style.visibility="hidden"

It should work either way. Perhaps you have a typo in the full code you're running. If you post the code maybe we can figure out what's going on... ;)

---

### Post by bb002 on 2007-05-15
I get this error too with firefox but it works as expected in Internet Explorer....it really is quite annoying. Haven't test any other browser.

---

### Post by tc101 on 2007-05-15
> Perhaps you have a typo in the full code you're running.

> I get this error too with firefox

Good to know that, because I have looked at it again and again and see no typos.

---

