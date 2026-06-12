---
title: "XML Display"
date: 2010-01-17
forum: Programming Talk
---

### Post by Tp2357 on 2010-01-17
Hi!

I am working on a program that will take an XML document, and display it using HTML... Could I get some help?

---

### Post by Arndt on 2010-01-17
> **Tp2357 said:**
> Hi!

I am working on a program that will take an XML document, and display it using HTML... Could I get some help?

What kind of help do you need?

Have you chosen the programming language? Do you know how it should be presented on the page? The same way as xmllint --format does?

---

### Post by wmcbrine on 2010-01-17
XSLT and CSS are your friends.

---

### Post by Tp2357 on 2010-01-17
Mainly I need help with the theory of the code to accomplish it. I am amazing with HTML, and okay with Javascript. Is it possible to accomplish it with these languages?

---

### Post by Reiger on 2010-01-17
If you want to do the following:

take XML Doc -> process -> get &#8216;webpage&#8217; (HTML tree); then XSLT + CSS is definitely the way to go.

If you want to do the following:

inject XML Doc from some source into webpage as styled text; then you can do this with JavaScript. In fact, there is a [SyntaxHighlighter]("http://alexgorbatchev.com/wiki/SyntaxHighlighter") ready made for the purpose, and it works with more than just XML.

---

