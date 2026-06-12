---
title: "Centering a Container of Floating Divs"
date: 2010-06-07
forum: Programming Talk
---

### Post by Ryland Taylor on 2010-06-07
Lets say I have these two files...
**index.html**:
```
<html>
<head>
<link rel="stylesheet" type="text/css" href="style.css" />
</head>
<body>
<div id="container">
<div id="sidebar"></div>
<div id="main"></div>
</div>
</body>
</html>
```

**style.css**:
```
#container
{
    width: 960px;
    float: left;
}
#sidebar
{
    width: 15%;
    float: left;
}
#main
{
    width: 80%;
    float: left;
}
```

What if I want to center the containing div? If I put margin left and right as auto, and take out float left for the container, It messes it up.

---

### Post by mo.reina on 2010-06-07
text-align:center doesn't work?

```
#container
{
    width: 960px;
    text-align: center;
    position: relative;
}

```

---

### Post by Ryland Taylor on 2010-06-07
No, that centers everything inside the container. What I am trying to do is make it so the containing div is in the center of the page. Sorry if I was unclear.

---

### Post by trent.josephsen on 2010-06-07
margin:auto should center the box within its containing element unless you are using an archaic version of IE (in which case the text-align trick should work).  What do you mean by "messes it up"?  How does what happens differ from what you expected to happen?

---

### Post by Ryland Taylor on 2010-06-07
By "messes it up," I meant that since the sidebar and main divs are "floating" above the container, the container does not expand with the sidebar and main divs as they get taller. The sidebar and main divs expand outside of the border of the container, while the container stays at its original height.
Normally I'm more descriptive than "messes it up," but I was in a hurry at the time

---

### Post by trent.josephsen on 2010-06-07
Untested, but it should work:  put another <div> inside the container, after the floated elements and all the other contents of the element, with style clear:both.  It will move to the bottom of both the floated elements and expand your container div.  Unless I'm still misunderstanding.

---

### Post by mo.reina on 2010-06-07
> **Ryland Taylor said:**
> No, that centers everything inside the container. What I am trying to do is make it so the containing div is in the center of the page. Sorry if I was unclear.

you can set the margin and width:

```
width: 60%;
left: 20%;
```

that should center the container, of course if the values are differet, ex. your width is 75% then left margin would be 12.5%, etc.

---

### Post by v8YKxgHe on 2010-06-08
Remove the 'float' property from #container and read about the 'overflow' property, 'hidden' is most likely the value you'll want.

Btw, why are you not using a doctype? Doing so will result in the browser rendering in quirks mode. If you want HTML5 (which I'd advise) use '<!DOCTYPE HTML>'

---

### Post by Ryland Taylor on 2010-06-08
I am using a doctype, The code I posted isn't the real code, It's just a basic example I posted so people would get the Idea. If I posted all the code for the website, it might be a little harder to scan through and see what I'm talking about.

EDIT: The "clear: both;" worked! Thanks for all the help!

---

