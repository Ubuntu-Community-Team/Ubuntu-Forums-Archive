---
title: "div id variable and javascript"
date: 2011-08-30
forum: Programming Talk
---

### Post by maclenin on 2011-08-30
I have a LARGE number of thumbnail images, which I'd like to display in a web-based gallery format.

I currently have a div defined for the first few thumbnails. There are 400 thumbnails.
```
<div id="gallery1"><img src="thumbnail1" id="t1" /></div> 
<div id="gallery2"><img src="thumbnail2" id="t2" /></div>
<div id="gallery3"><img src="thumbnail3" id="t3" /></div>
<div id="gallery4"><img src="thumbnail4" id="t4" /></div>
<div id="gallery5"><img src="thumbnail5" id="t5" /></div>
...
<div id="gallery400"><img src="thumbnail400" id="t400" /></div>
```

As I have 400 images, **I am trying to come up with a method to create a generic "gallery1" div whose "id" can be changed, dynamically, using javascript**, in much the same way that color, src, background and innerHTML can be manipulated.

My hope is that I can hard-code ONE gallery div in the html (seems I'll have to define all 400 in the css) and then generate (dynamically) additional "virtual" divs to accommodate the other 399 thumbnails...

A. **HTML**
```
<div id="gallery1"><img src="thumbnail1" id="t1" /></div> 
```

B. **JAVASCRIPT**
```
for (i=0; i<number_of_thumbmails; i++)
{
document.getElementById("gallery1").id="gallery"+[i+1];
document.getElementById("t1").id="t"+[i+1];
}
```

C. ...yielding:
```
<div id="gallery1"><img src="thumbnail1" id="t1" /></div> <!--hard-coded in html-->
[COLOR="Gray"]<div id="gallery2"><img src="thumbnail2" id="t2" /></div> <!--defined via javascript-->
<div id="gallery3"><img src="thumbnail3" id="t3" /></div> <!--defined via javascript-->
<div id="gallery4"><img src="thumbnail4" id="t4" /></div> <!--defined via javascript-->
<div id="gallery5"><img src="thumbnail5" id="t5" /></div> <!--defined via javascript-->
... 
<div id="gallery400"><img src="thumbnail400" id="t400" /></div> <!--defined via javascript-->[/COLOR]
```

Thanks for any insight!

---

### Post by ofnuts on 2011-08-30
```

<script type="text/javascript">
for (i=1;i<=400;i++)
{
    var num="00"+i;
    var id=num.slice(-3);
    document.write("<div id=\"gallery"+id+"\">"+id+" <img id=\"ts"+id+"\" src=\"thumb"+id+".jpg\" /></div>");
}
</script>

```Or am I missing something?

---

### Post by maclenin on 2011-08-30
**ofnuts** - thanks for the code (and great idea!) - it looks like your solution writes 400 sequential "hard copies" of <div id="gallery"> - and though that would certainly save me typing time as I assemble the html, what I am actually trying to do is create no more than ONE hard coded line of code in the html, which I then replicate n times - virtually - via javascript.

One can dynamically (and temporarily) change the values of (i.e. ***not*** document.write) src and other attributes/properties (innerHTML, for example), with reference to a unique id. What I am trying to accomplish - if it's even possible - is the virtual (temporary) replication of the entire line of html code - through temporary modification of the ids (via JS)...
```
**<div id="Hard-coded_g01"><img src="" id="Hard-coded_t01" /></div>**
[B][COLOR="Silver"]<div id="JS-defined_g02"><img src="JS-defined" id="JS-defined_t02" /></div>
<div id="JS-defined_g03"><img src="JS-defined" id="JS-defined_t03" /></div>
<div id="JS-defined_g04"><img src="JS-defined" id="JS-defined_t04" /></div>
<div id="JS-defined_g05"><img src="JS-defined" id="JS-defined_t05" /></div>
<div id="JS-defined_g06"><img src="JS-defined" id="JS-defined_t06" /></div>[/COLOR][/B]

```

...and then dynamic association of images and other functionality (also via javascript) with both the single **Hard-coded** and "n" virtual / **JS-defined** (uniquely/temporarily) id'ed lines of code....

**function one()** {dynamically modify the hard-coded ids - creating an n number of additional unique virtual ids}
**function two()** {assign temporary values to src with reference to the hard-coded and virtually created ids}

Perhaps I am dreaming....

---

### Post by ofnuts on 2011-08-30
> **maclenin said:**
> **ofnuts** - thanks for the code (and great idea!) - it looks like your solution writes 400 sequential "hard copies" of <div id="gallery"> - and though that would certainly save me typing time as I assemble the html, what I am actually trying to do is create no more than ONE hard coded line of code in the html, which I then replicate n times - virtually - via javascript.

No... put that code in your HTML, and it will dynamically generate the divs when the page is loaded. My whole test HTML looked like:

```

<html>
<body>
<script type="text/javascript">
for (i=1;i<=400;i++)
{
    var num="00"+i;
    var id=num.slice(-3);
    document.write("<div id=\"gallery"+id+"\">"+id+" <img id=\"ts"+id+"\" src=\"thumb"+id+".jpg\" /></div>");
}
</script>
</body>
</html>

```

---

### Post by maclenin on 2011-08-31
Stunning!

**Yes**...worked exactly as described!

Thanks, **ofnuts**!

P.S. Can you direct me to any resources which might help me learn what you've learned me?

---

### Post by ofnuts on 2011-08-31
> **maclenin said:**
> Stunning!

**Yes**...worked exactly as described!

Thanks, **ofnuts**!

P.S. Can you direct me to any resources which might help me learn what you've learned me?

That's Javascript 101... any doc will do (I know very little Javascript)

---

### Post by maclenin on 2011-08-31
...maybe, but what you know, you know well...thanks, again....

---

