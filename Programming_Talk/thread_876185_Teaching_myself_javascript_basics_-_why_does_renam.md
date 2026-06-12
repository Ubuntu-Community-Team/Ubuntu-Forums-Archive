---
title: "Teaching myself javascript basics - why does renaming file's extension to xhtml break"
date: 2008-07-31
forum: Programming Talk
---

### Post by spaceballl on 2008-07-31
Hi all,

Sorry I didn't have enough characters in the heading to finish my thought. I'm trying to teach myself some basics of javascript, and how to embed currently written javascript into my code. I'm using the lightbox2 framework right now, and I think the effects it produces are really cool. But i'm confused...

If I make and "index.html" file, and put in some sample code (sample code at the bottom of the post), it works! However, if I take the exact same code, and rename the file extension to xhtml, it doesn't work anymore! Am I missing something? Full html below - thanks!

```


<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
        "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en">
<head>	
	<title>Lightbox JS v2.0 | Test Page</title>
	<link rel="stylesheet" href="/css/test.css" type="text/css" media="screen" />
	<script src="/lightbox/js/prototype.js" type="text/javascript"></script>
	<script src="/lightbox/js/scriptaculous.js?load=effects,builder" type="text/javascript"></script>
	<script src="/lightbox/js/lightbox.js" type="text/javascript"></script>
</head>
<body>

<a href="/lightbox/images/image-1.jpg" rel="lightbox"><img src="/lightbox/images/thumb-1.jpg" width="100" height="40" alt="" /></a>


</body>
</html>


```

---

### Post by mssever on 2008-07-31
It probably has something to do with the mime type it's being served with and that type's interaction with your browser.

---

### Post by LaRoza on 2008-07-31
> **spaceballl said:**
> 
Sorry I didn't have enough characters in the heading to finish my thought. I'm trying to teach myself some basics of javascript, and how to embed currently written javascript into my code. I'm using the lightbox2 framework right now, and I think the effects it produces are really cool. But i'm confused...

You shouldn't embed script into the XHTML. It should be separate. See [http://laroza.freehostia.com](http://laroza.freehostia.com) and all the links on it. It all works without any script mixed with the markup.

> 
However, if I take the exact same code, and rename the file extension to xhtml, it doesn't work anymore! Am I missing something? Full html below - thanks!


That doesn't help.

[list]
[*] What doesn't work?
[*] What is the error?
[*] What gives you the error?
[/list]

---

### Post by spaceballl on 2008-07-31
As far as "what doesn't work," this is just a VERY simple page using publicly available javascript. A small thumbnail is displayed and when I click it, the image expands with animation the background of the web browser darkens to highlight the image. So, with the *.html extension, works just fine. When I move to a *.xhtml extension, the page loads fine. It looks normal, but clicking on the image gives me no animation - thanks for the help!

---

### Post by mssever on 2008-07-31
> **spaceballl said:**
> As far as "what doesn't work," this is just a VERY simple page using publicly available javascript. A small thumbnail is displayed and when I click it, the image expands with animation the background of the web browser darkens to highlight the image. So, with the *.html extension, works just fine. When I move to a *.xhtml extension, the page loads fine. It looks normal, but clicking on the image gives me no animation - thanks for the help!
Have you checked the things I mentioned in my earlier post? Have you tried a different browser? Have you used the Firebug extension to poke around?

---

### Post by drubin on 2008-07-31
> **LaRoza said:**
> You shouldn't embed script into the XHTML. It should be separate. See [http://laroza.freehostia.com](http://laroza.freehostia.com) and all the links on it. It all works without any script mixed with the markup.


Is that not what the OP is doing?

---

### Post by LaRoza on 2008-07-31
> **rubinboy said:**
> Is that not what the OP is doing?

In the example, yes, but the post mentions embeding it.

---

