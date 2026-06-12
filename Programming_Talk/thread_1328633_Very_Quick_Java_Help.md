---
title: "Very Quick Java Help"
date: 2009-11-16
forum: Programming Talk
---

### Post by easybake on 2009-11-16
Hello I'm fairly new to java but I am learning quick.

I am working on a website that uses .tpl files mainly to control content on pages. 

Currently I am running this:

```
<a href="#"
onclick="document.getElementById('text1').style.display='block';">Question numero uno</a>
<div id="text1" style="display:none;">
This text is revealed by button 1 and hidden by button 3.
<a href="#"
onclick="document.getElementById('text1').style.display = 'none';">
hide</div></a>
```

The question is clicked, the answer shows, and they have the option to hide it again.

I would much rather have the person click the question again to hide the answer and not have to click "hide"

Since I am dealing in .tpl files this code i found doesn't work at all > ```
<script type="text/javascript">
<!--
    function toggle_visibility(id) {
       var e = document.getElementById(id);
       if(e.style.display == 'block')
          e.style.display = 'none';
       else
          e.style.display = 'block';
    }
//-->
</script>

```
And the usage would be ```
<a href="#" onclick="toggle_visibility('foo');">Click here to toggle visibility of element #foo</a>
<div id="foo">This is foo</div>

```

I believe it would work if I could use a single line. Without having to establish variables. 

I was thinking ```
if{document.getElementById('text1').style.display='block' onclick="document.getElementById('text1').style.display='none'}
else onclick="document.getElementById('text1').style.display='block'}
```

but i can't figure out the proper usage.

---

### Post by MonoDeem on 2009-11-16
[php]
function toggleMe() {
    if (document.getElementById('text1').style.display == 'block') { 
        document.getElementById('text1').style.display = 'none';
    } else {
        document.getElementById('text1').style.display = 'block';
    }
}
[/php][php]<a href="#" onClick="toggleMe()">Question</a>
<div id="text1">Answer</div>[/php]

---

### Post by kavon89 on 2009-11-16
```
java != javascript && "Javascript".contains("Java");
```

True statement.

---

### Post by MonoDeem on 2009-11-16
> **kavon89 said:**
> ```
(java != javascript && "Javascript".contains("Java")) == true
```

```
[COLOR=Red]Error [1]: Undefined variable: java
Error [1]: Undefined variable: javascript[/COLOR]
```

---

### Post by kavon89 on 2009-11-16
> **MonoDeem said:**
> ```
[COLOR=Red]Error [1]: Undefined variable: java
Error [1]: Undefined variable: javascript[/COLOR]
```

Although I updated it, you're right it has errors.

```

!(Javascript instanceof Java) && "Javascript".contains("Java");

```

I'm not too sure if I used instanceof correctly if Javascript and Java were defined classes though. ;)

---

### Post by easybake on 2009-11-16
> **MonoDeem said:**
> [php]
function toggleMe() {
    if (document.getElementById('text1').style.display == 'block') { 
        document.getElementById('text1').style.display = 'none';
    } else {
        document.getElementById('text1').style.display = 'block';
    }
}
[/php][php]<a href="#" onClick="toggleMe()">Question</a>
<div id="text1">Answer</div>[/php]


I tried putting this into the .tpl that I work with. It caused the page to be completely blank. Is there a different way I can do this, or is there a special way I have to implement this code? I've tried wrapping the function in <?php  ?> but to no avail.

---

### Post by jespdj on 2009-11-17
[IMG]http://farm3.static.flickr.com/2614/3779250024_8713842620_o_d.png[/IMG]

---

### Post by The Cog on 2009-11-17
This works for me:
```
<html>
<script type="text/javascript">
<!--
    function toggle_visibility(id) {
       var e = document.getElementById(id);
       if(e.style.display == 'none')
          e.style.display = 'block';
       else
          e.style.display = 'none';
    }
//-->
</script>
<a href="#" onclick="toggle_visibility('foo');">Click here to toggle visibility of element #foo</a>
<div id="foo" style="display:none">This is foo</div>
</html>

```

---

### Post by mike_g on 2009-11-17
> document.getElementById('text1').style.display == 'block')
For some reason IE craps out sometimes with code like this. To hide IEs crappyness its best to do it the way The Cog did - getting the element as a variable first before doing things with it. Personally I like using [JQuery](http://jquery.com/) for this kind of stuff as you can add transition effects very easily. It also handles many of IE's issues, so I don't have to worry about them :)

---

### Post by easybake on 2009-11-17
> **jespdj said:**
> [IMG]http://farm3.static.flickr.com/2614/3779250024_8713842620_o_d.png[/IMG]

Lolol sorry java /= javascript. I am a huge noob to scripting.

But I'm still getting the issue, and I think that it is just the tools I have to work with. 

I have no doubt that the code would work in a normal situation but I think I have a different situation. I don't work with physical .tpl files, everything is online. It's a web based interface that 

The problem is, when I try and insert any type of setup that establishes variables I get a completely blank page. Is there anyway to write this as {if blank is true}onclick this..{else}onclick that.

---

### Post by easybake on 2009-11-17
Ahhhhh ](*,)](*,)

Apparently there is a main javascript file which I can insert the code. 

I just found it and have yet to try it out. Will I run into any issues with having multiple questions on one page? The javascript references (text1). And that is the div id of question 1. 

Will I have to make separate entries for each question. Like:
```
function toggleMe() {
    if (document.getElementById('**text1**').style.display == 'block') { 
        document.getElementById('**text1**').style.display = 'none';
    } else {
        document.getElementById('**text1**').style.display = 'block';
    }
}  


function toggleMe() {
    if (document.getElementById('**text**2').style.display == 'block') { 
        document.getElementById('**text2**').style.display = 'none';
    } else {
        document.getElementById('**text2**').style.display = 'block';
    }
}  
```

Or is there a simpler way.

---

### Post by easybake on 2009-11-17
Thanks for all the help everyone, I ended up going with this:```

function toggleMe(id) {
	var e = document.getElementById(id);
	if (e.style.display == 'block')
		e.style.display = 'none';
	else
		e.style.display = 'block';
}
```

```
<a href="#" onclick="toggleMe('text1');">Question</a>
<div id="text1" style="display:none;">Answer
```


The help was much appreciated, I know it can be tough dealing with noobs, like me, who have no idea what they are talking about.

---

