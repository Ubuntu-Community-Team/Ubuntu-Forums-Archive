---
title: "IE7 RightToLeft Issues"
date: 2009-11-09
forum: Programming Talk
---

### Post by ve4cib on 2009-11-09
At work I'm working on translating a product into Arabic for one of our clients*.  The product is a web application that displays editable maps and the like.  We're using [ExtJS](http://www.extjs.com/) for the UI.  I've had to reverse-engineer most of the default ExtJS CSS files to make the UI work for a right-to-left language, and it works just fine in Opera, Chrome, Firefox, and IE8.  The problem is IE7... (big surprise there :P)

I think the problem is best-described with a couple of pictures.  When the user opens a window sometimes (not always, but most of the time) all of the contents are misaligned way off to the left:

[img]http://ubuntuforums.org/attachment.php?attachmentid=135461&stc=1&d=1257781004[/img]

Clicking and dragging on the window just a little bit magically forces all the elements to realign themselves:

[img]http://ubuntuforums.org/attachment.php?attachmentid=135462&stc=1&d=1257781004[/img]

The only CSS change that happens when the window is moved is the absolute positioning of the container; all of the contents' CSS attributes stay the same.

I've tried adding a listener to the window's "show" event to programatically force move the window when it's drawn, but that doesn't work.  I've also tried tweaking a CSS property of some content element to force a refresh whenever the window is shown, but that didn't work either.

Has anyone ever run into similar RTL alignment issues in IE7?  Or do you have any good URLs with suggested work-arounds.  I don't care how hacky the solution is, as long as it works.  I've tried QuirksMode, but I didn't find anything that looked like it would help there.


____________
* I'm only translating the UI; someone else is responsible for the Arabic text, so please ignore any Arabic writing that doesn't make any sense

---

### Post by A_Fiachra on 2009-11-09
What does this have to do with a Linux distro???

---

### Post by ve4cib on 2009-11-09
> **A_Fiachra said:**
> What does this have to do with a Linux distro???

Nothing at all.  But to quote the header at the top of this page...

> **Programming Talk**
This forum is for all programming questions.
The questions do not have to be directly related to Ubuntu and any programming language is allowed.

---

