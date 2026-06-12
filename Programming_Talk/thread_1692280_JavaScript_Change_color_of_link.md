---
title: "JavaScript: Change color of link"
date: 2011-02-21
forum: Programming Talk
---

### Post by yc2 on 2011-02-21
Hello,

How do I change the color of the links within a div (here with id='myID') _using JavaScript_ ('dynamically')?

(I am referring to changing the basic color OR the color on hovering. I am NOT referring to the colorshift on/off hovering.)

The way I tried was no good:
```
document.getElementById('myID').A:link.color = '#0000a0';
document.getElementById('myID').A:visited.color = '#0000a0';

```
lower case "a:visited" not good either

Thanks

---

### Post by nvteighen on 2011-02-21
Why not use CSS? It's much easier... :/

---

### Post by lykeion on 2011-02-21
I agree with nvteighen, use CSS.
Otherwise something like this:
```
var nodesArray = document.getElementById('myID').getElementsByTagName('a');
for (var i = 0; i < nodesArray.length; i++) {
    nodesArray[i].style.color = 'red';
}
```

---

### Post by ve4cib on 2011-02-21
Personally what I'd do is something like this:
*(appologies for any syntax errors I've missed)*

HTML:
```

<div id="myID" class="myId-normal">
    <a...>
    <a...>
    <a...>
</div>

```

CSS:
```

.myId-normal a {
    color: #000000;
}

.myId-alternate a {
    color: #ff0000;
}

```

JS:
```

function changeColour() {
    var myDiv = document.getElementById('myDiv');
    myDiv.className = 'myId-alternate';
}

function resetColour() {
    var myDiv = document.getElementById('myDiv');
    myDiv.className = 'myId-normal';
}

```


Basically you're defining two CSS classes for the div; the normal one and the alternative one.  Your JS then dynamically changes the CSS class of the div.  This will automatically change the colours of your links (from black to red and vice-versa in my example).

---

### Post by yc2 on 2011-02-22
Thanks a lot for two useful approaches.

Using getElementsByTagName I think it is not possible to reach the pseudoclasses for the a-tag (link/visited/hover/active) separately? Or is it? (You can't set a separate color for hover, f.ex?)

Shifting class makes pseudoclasses available individually.

(I think there is a small typo, as warned for, in the "shifting class ex." document.getElementById('myDiv') should be document.getElementById('myID'))

```
<style>
#myID {}
#myID a:link {color: blue;}
#myID a:visited {color: blue;}
#myID a:hover {color: yellow;}
</style>

<script type="text/javascript">
function changeColour_01 () {
	var nodesArray = document.getElementById('myID').getElementsByTagName('a');
	for (var i = 0; i < nodesArray.length; i++) {
	    nodesArray[i].style.color = 'red';
	}
}
function resetColour_01 () {
	var nodesArray = document.getElementById('myID').getElementsByTagName('a');
	for (var i = 0; i < nodesArray.length; i++) {
	    nodesArray[i].style.color = 'blue';
	}
}
</script>

<a href="javascript:changeColour_01()">changeColour_01()</a><br>
<a href="javascript:resetColour_01()">resetColour_01()</a><br>


<br>
<br>
<div id="myID" class="myID-normal">
<a href="http://ubuntuforums.org">UF</a>
</div>


<br>
<br>
---------------------------------------------------------------------------------
<br>
<br>


<style>
#myID_02 {}

.myID_02-normal a:link {color: green;}
.myID_02-normal a:visited {color: green;}
.myID_02-normal a:hover {color: purple;}

.myID_02-alternate a:link {color: orange;}
.myID_02-alternate a:visited {color: orange;}
.myID_02-alternate a:hover {color: black;}
</style>

<script type="text/javascript">
function changeColour_02() {
    var myDiv = document.getElementById('myID_02');
    myDiv.className = 'myID_02-alternate';
}
function resetColour_02() {
    var myDiv = document.getElementById('myID_02');
    myDiv.className = 'myID_02-normal';
}
</script>

<a href="javascript:changeColour_02()">changeColour_02()</a><br>
<a href="javascript:resetColour_02()">resetColour_02()</a><br>

<br>
<div id="myID_02" class="myID_02-normal">
<a href="http://ubuntuforums.org">UF</a>
</div>

```


Maybe just a detail, I didn't understand this:
> I agree with nvteighen, use CSS.
I thought all this was CSS (through JavaScript) or is there some other "CSS-method" too?

Thanks a lot.

---

