---
title: "CSS: Firefox div height percentages"
date: 2006-07-13
forum: Programming Talk
---

### Post by ironfistchamp on 2006-07-13
Hey I want to set the height of a div with a percentage. I am aiming to get the div to be 70% tall min and expand to fit content. So far all I have is a tiny box with one word "CONTENT". I tried setting height and min-height. That didn't work. I tested in IE6 and it was fine with jsut stating the height. What do I need to do for firefox?

Thanks

Ironfist

---

### Post by kripkenstein on 2006-07-13
I'm no expert, but try using a table instead of a div, a table with one row&column:

<table height="70%"><tr><td> ... </td></tr></table>

- see if that works.

---

### Post by ironfistchamp on 2006-07-13
*sharp intake of breath* Ooh tables. I am trying to avoid them. But I shall use that as a last resort thanks.

---

### Post by Jasper Houtman on 2006-07-13
Did you try setting the height in your stylesheet?
for example:
```
div ....
{
height: 70%
}
```

Not sure if that's the proper way to set it, might want to look it up on a site like [w3schools]("http://www.w3schools.com")

---

### Post by Jasper Houtman on 2006-07-13
Apologise for the double post, but may have a solution.

First define your div's
[HTML]

<div class="left">
	Left content
</div>
<div class="top">
	Top content
</div>
<div class="main">
	Main content
</div>[/HTML]

Add to stylesheet

```


div.left {
	position: absolute;
	top: 0px;
	left: 0px;
	width: 200px;
	height: 70%;
}

div.top {
	position: absolute;
	top: 0px;
	left: 200px;
	width: 580px;
	height: 20%;
}

div.main {
	position: absolute;
	top: 150px;
	left: 200px;
	width: 580px;
	height: 50%;
}

```

Then put everything in a container:

[HTML]
<div class="container">
	<div class="left">
		Top content
	</div>
	etc.
</div>
[/HTML]

And define the container in your stylesheet:

```

div.container {
	position: relative;
	margin: 0 auto;
	width: 780px;
	height: 70%;
}

```

Might need a bit of tinkering but should work.

---

### Post by ironfistchamp on 2006-07-13
Thanks I shall try it out. :)

Edit: Had a go. Didn't change anything it seems. I'm not good enough to tinker and get it working. I don't know what changes might do things. Thanks though

---

### Post by bieber on 2006-07-13
The trick is that for the height property to be valid for a div, every containing element must also have a height property.  That means html, body, and any containing divs must have a height specified in the stylesheet (auto if you don't want to specify a specific height for them).

---

### Post by ironfistchamp on 2006-07-14
Thanks that got it working. Top notch :D

---

