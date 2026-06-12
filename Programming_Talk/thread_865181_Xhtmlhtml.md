---
title: "Xhtml/html"
date: 2008-07-20
forum: Programming Talk
---

### Post by shifty2 on 2008-07-20
I was already under the impression the XHTML was where the web was heading, yet recently have seen a lot suggesting that infact XHTML is not handled properly by web browsers. 

What is the consensus here, use XHTML or HTML?

---

### Post by LaRoza on 2008-07-20
XHTML.

The only browsers that can't handle it fail when it is sent with the mime type other than text/html. (See my site, it works in all used browsers, yet is XHTML 1.1)

---

### Post by elithrar on 2008-07-20
I'd suggest reading:

[http://www.tangerinesmash.com/writings/2007/jun/11/html-vs-xhtml-best-tool-job/](http://www.tangerinesmash.com/writings/2007/jun/11/html-vs-xhtml-best-tool-job/)
[http://webkit.org/blog/68/understanding-html-xml-and-xhtml/](http://webkit.org/blog/68/understanding-html-xml-and-xhtml/) &
[http://www.b-list.org/weblog/2008/jun/18/html/](http://www.b-list.org/weblog/2008/jun/18/html/)

... before making your mind up.

> **LaRoza said:**
> 
The only browsers that can't handle it fail when it is sent with the mime type other than text/html. (See my site, it works in all used browsers, yet is XHTML 1.1)

You're serving it as [FONT="Courier New"]application/xhtml+xml[/FONT] according to your own meta tag (and what Firefox says) - not that I'm complaining, because at least it's now being handled by an XML parser & not the HTML parser (which is what happens when it's served as [FONT="Courier New"]text/html[/FONT]).

---

### Post by LaRoza on 2008-07-20
> **elithrar said:**
> 
You're serving it as [FONT="Courier New"]application/xhtml+xml[/FONT] according to your own meta tag (and what Firefox says) - not that I'm complaining, because at least it's now being handled by an XML parser & not the HTML parser (which is what happens when it's served as [FONT="Courier New"]text/html[/FONT]).
The server isn't ;)

Firefox, Opera and other compliant browsers recognize it because of that, but legacy browsers like IE see the server serving HTML and ignore what they don't know.

---

