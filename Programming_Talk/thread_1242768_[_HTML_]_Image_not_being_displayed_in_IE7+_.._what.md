---
title: "[ HTML ] Image not being displayed in IE7+ .. what's the reason ?"
date: 2009-08-17
forum: Programming Talk
---

### Post by credobyte on 2009-08-17
```
<img src="images/logo3.jpg" border="1px" alt="VillExchange"/>

```Mozilla Firefox, Opera, Avant, etc. - all browsers know what it means and show my image correctly, however, IE7+ browsers show a red cross ( eg. image missing ). When I click Properties, I see a full path ( correct one ) to my image.

What could cause this problem ? Could web page encoding be the reason ?

---

### Post by hessiess on 2009-08-17
> **credobyte said:**
> ```
<img src="images/logo3.jpg" border="1px" alt="VillExchange" />

```Mozilla Firefox, Opera, Avant, etc. - all browsers know what it means and show my image correctly, however, IE7+ browsers show a red cross ( eg. image missing ). When I click Properties, I see a full path ( correct one ) to my image.

What could cause this problem ? Could web page encoding be the reason ?

try puting a space between the last quote and the ">".

---

### Post by credobyte on 2009-08-17
> **hessiess said:**
> try puting a space between the last quote and the ">".

Doesn't make any sense + image still not visible.

---

### Post by wojox on 2009-08-17
try border="1" it may be the px ie's not understanding.
If that doesn't work remove the border. It defaults at 1 if I remember correctly.

---

### Post by wmcbrine on 2009-08-17
Unless this is an XHTML page (with a proper XHTML DOCTYPE and MIME type), take out the slash before the closing bracket. I dunno if that's the issue, but it's not correct HTML.

Oh, also this: '[The "align", "border", "hspace", and "vspace" attributes of the image element were deprecated in HTML 4.01, and are not supported in XHTML 1.0 Strict DTD.](http://www.w3schools.com/tags/tag_IMG.asp)' I hope "not supported" doesn't translate to "the picture won't be rendered at all", but...

---

### Post by credobyte on 2009-08-17
> **wmcbrine said:**
> Unless this is an XHTML page (with a proper XHTML DOCTYPE and MIME type), take out the slash before the closing bracket. I dunno if that's the issue, but it's not correct HTML.

Oh, also this: '[The "align", "border", "hspace", and "vspace" attributes of the image element were deprecated in HTML 4.01, and are not supported in XHTML 1.0 Strict DTD.]("http://www.w3schools.com/tags/tag_IMG.asp")' I hope "not supported" doesn't translate to "the picture won't be rendered at all", but...

Everything works perfectly - I've approximately 20 images ( all added in the same style ) all over the page and only 1 image ( header ) is not working .. wtf ? :-#
[COLOR=Gray]P.S. - XHTML 1.0[/COLOR]

---

### Post by knopper67 on 2009-08-17
> **credobyte said:**
> IE7+

Well, there's your problem.

---

### Post by credobyte on 2009-08-17
> **knopper67 said:**
> Well, there's your problem.

~      15.9% IE7 uses all over the world - *my* problem ?

---

### Post by jeffathehutt on 2009-08-17
I wonder if the file itself became corrupt somehow.  Perhaps there is a corrupt header in that image, and firefox and others are just skipping over the broken header and showing the image anyway.  IE may be unable to make sense of the header, and thus doesn't show anything.  Since all your other images are working, this is a possible case.

Try opening the image in the gimp or another program and re-saving it.  If that doesn't help, try opening the image directly from IE through the file menu.  Hopefully that will fix it, or at least narrow down the possible problems.

---

### Post by credobyte on 2009-08-17
> **jeffathehutt said:**
> I wonder if the file itself became corrupt somehow. Perhaps there is a corrupt header in that image, and firefox and others are just skipping over the broken header and showing the image anyway. IE may be unable to make sense of the header, and thus doesn't show anything. Since all your other images are working, this is a possible case.
 
Try opening the image in the gimp or another program and re-saving it. If that doesn't help, try opening the image directly from IE through the file menu. Hopefully that will fix it, or at least narrow down the possible problems.
 
I made it on Photoshop, re-saved via Paint and Gimp ( after changing a few things in it ) .. So far I've tried 3 file versions ( one of them was a mockup, containing only gradient ) - none of them seems to be ok @ IE7+.

---

### Post by Can+~ on 2009-08-17
Weird issue, could you show all the .html, or link to the website?

Also, I hope you're using CSS and not just dumping all the styling directly on html.

---

### Post by Warren Watts on 2009-08-17
I have had issues with IE displaying unexpected results when working with CSS and the like, and I have had some success in resolving the issues by making sure I had a proper doctype declaration at the beginning of the HTML document.

Here's a short article from the W3 Consortium on declaring doctypes:
[B][URL="http://www.w3.org/QA/Tips/Doctype"]
Don't forget to add a doctype[/URL][/B]

---

### Post by credobyte on 2009-08-17
> **Can+~ said:**
> Weird issue, could you show all the .html, or link to the website?

Also, I hope you're using CSS and not just dumping all the styling directly on html.

Sorry, I can't provide the source code / live link ( NDA ). About CSS - I've always used .css files ;)

> **Warren Watts said:**
> I have had issues with IE displaying unexpected results when working with CSS and the like, and I have had some success in resolving the issues by making sure I had a proper doctype declaration at the beginning of the HTML document.

Here's a short article from the W3 Consortium on declaring doctypes:
[B][URL="http://www.w3.org/QA/Tips/Doctype"]
Don't forget to add a doctype[/URL][/B]

Doctype is being added automatically ( like it's shown in the link above ).

---

### Post by soltanis on 2009-08-18
This wouldn't be the first time Internet Explorer had a bug, you know. I doubt if this displays correctly within every other browser that it is or should be your HTML to blame.

---

### Post by credobyte on 2009-08-18
> **soltanis said:**
> This wouldn't be the first time Internet Explorer had a bug, you know. I doubt if this displays correctly within every other browser that it is or should be your HTML to blame.

That's only on IE7+ browsers. Anyway, I fixed it by replacing JPEG ( .jpg ) with PNG.

---

