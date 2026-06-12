---
title: "css/javascript issue with style.background in firefox"
date: 2007-01-20
forum: Programming Talk
---

### Post by tocleora on 2007-01-20
[SIZE="3"]I have a piece of code that works in IE but I can't get to work in firefox.  I realize a lot of people think tables are bad so I'm open to whatever way I can do this that it will work.  The first piece of code I run is:

```
<td width="300" height="150" background="images/headerback_02.jpg" id="bubblecell">
```

and then at the end of the page I have this:

```
setTimeout('document.getElementById("bubblecell").style.background=url("images/headerbubble.jpg");',10000);
```

I've tried it "("bubblecell").background", I've tried it "url(images/headerbubble.jpg)"... I'm stumped. :)  Thanks![/SIZE]

---

### Post by Burgresso on 2007-01-20
Your table element has its background set with HTML, not CSS. Try this:

```
<td width="300" height="150" style="background-image: url("images/headerback_02.jpg);" id="bubblecell">
```

---

### Post by Grey on 2007-01-20
Do this instead.

```
<div style="width:300;height:150;background-image:url(images/headerback_02.jpg)" id="bubblecell"></div>
```

No html 3.2.  No tables.  I'm happy about that.  :)

---

### Post by tocleora on 2007-01-20
[SIZE="2"]> **Grey said:**
> Do this instead.

```
<div style="width:300;height:150;background-image:url(images/headerback_02.jpg)" id="bubblecell"></div>
```

No html 3.2.  No tables.  I'm happy about that.  :)

That's great I'm more than happy to learn how to do it without tables, however, I'm confused as to how this knows where to be on the web page, in this case, the right side of the main header graphic, and without tables how will I also tell the browser where the content goes, like:

```
<table><tr><td>left part of header </td><td>right part of header</td></tr><tr><td colspan="2">Content of the page</td></tr></table>
``` 

How would I do the same with div that it's positioned the same across multiple os's and browsers?[/SIZE]

---

### Post by tocleora on 2007-01-20
> **Burgresso said:**
> Your table element has its background set with HTML, not CSS. Try this:

```
<td width="300" height="150" style="background-image: url("images/headerback_02.jpg);" id="bubblecell">
```

Hmmm, unfortunately that didn't do it. :(  I should also mentioned I tried this, this code at the top of the page:

```
	bubbleimg = new Image();
	bubbleimg.src = "images/headerbubble.jpg";
```

And this at the bottom instead:

```
setTimeout("document.getElementById('bubblecell').style.background = bubbleimg.src;",10000);
```

That doesn't work either. :(

---

### Post by tocleora on 2007-01-20
I got it working. Apparently I needed quotes around the url tag:

```
document.getElementById("bubblecell").style.background= "url('images/headerbubble.jpg')";
```

I'd still like to know how to write the equivalent of this with div's (or span's?) instead if anyone is willing to assist:

```
<center><table width="800">
<tr>
	<td width="500">Left Header Graphic</td>
	<td width="300">Right Header Graphic</td>
</tr>
<tr>
	<td colspan="2" width="800">Content of the page</td>
</tr>
</table>
</center>
```

---

### Post by Mirrorball on 2007-01-20
You have to think "semantically." Forget for a while how you want it to look like and concentrate on what it means. Think only about the meaning. Is it a header? A navigation list? Is it a footer? Or the main content area? Then choose the appropriate mark up. Don't use <center>, <big>, <b>, because they don't have any meaning. Choose <p>, <em>, <div id="footer"> etc. Then create the style sheet that will make your page look like you want. I must say, you have a lot to learn. Good web design isn't easy at all, mostly because different browsers have different bugs (and Internet Explorer has the most bugs).

---

### Post by tocleora on 2007-01-20
No, I'm not new to web design, just old school. :)  I do css and javascript now I'm just not real familiar with the positioning aspect of it where you would position things on the page and it look the same on all (major) screen resolutions, browsers and operating systems.  Is there a quick and dirty to the point resource out there?

In fact, if someone could just show me exactly how the equivalent of that table code above would look in css I'm sure I could figure it out just from that.  Possibility?

---

### Post by Mirrorball on 2007-01-21
HTML (rename the divs):
```

<body>
<div id="left_column"><!-- This should have a *meaningful* name, like "secondary content." -->
Left Header Graphic
</div>
<div id="right_column"><!-- This should have a *meaningful* name, like "secondary content." -->
Right Header Graphic
</div>
<div id="content">
Content of the page
</div>
</body>

```

And the CSS:
```

body {
    width: 800px; /* Not ideal, search for "fluid layout." */
}

#left-column {
    width: 61.5%;
    float: left;
    padding: 0;
    margin: 0 0 0 0.5%;
    border: none;
}

#right-column {
    width: 36.5%;
    float: right;
    padding: 0;
    margin: 0 0.5% 0 0;
    border: none;
}

#content {
    clear: both;
}

```

---

### Post by tocleora on 2007-01-21
Awesome! You Rock! :)  Thanks!

---

