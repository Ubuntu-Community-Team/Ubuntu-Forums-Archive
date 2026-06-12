---
title: "A good Python book for manipulating XML!"
date: 2008-07-17
forum: Programming Talk
---

### Post by rivalslayer on 2008-07-17
Can anyone suggest me a good book for manipulating XML with Python? Need it!:confused:

---

### Post by ceclauson on 2008-07-17
I don't know if this is helpful, but Python supports DOM (document-object model), which is a language-independent API for working with XML.

This means that if you understand how DOM works, it works the same in any language, so you should be able to use it in any language.  For instance, I first used DOM in Java, and have since been able to apply it in C++ and Python.

I googled a page with an introduction:
[http://www.boddie.org.uk/python/XML_intro.html](http://www.boddie.org.uk/python/XML_intro.html)

I hope this was helpful.

-Cooper

---

### Post by LaRoza on 2008-07-17
[http://docs.python.org/lib/markup.html](http://docs.python.org/lib/markup.html)

---

### Post by Wybiral on 2008-07-17
Use [elementtree]("http://docs.python.org/lib/module-xml.etree.ElementTree.html"), it's in the standard library and it's the most "pythonic" way to go about it.

---

### Post by LaRoza on 2008-07-17
> **Wybiral said:**
> Use [elementtree]("http://docs.python.org/lib/module-xml.etree.ElementTree.html"), it's in the standard library and it's the most "pythonic" way to go about it.

Use the DOM because it is the most standard way...

---

### Post by ghostdog74 on 2008-07-17
look for Python & XML [here](http://slav0nic.org.ua/static/books/python/) before its gone

---

### Post by babacan on 2008-07-17
> **ghostdog74 said:**
> look for Python & XML [here](http://slav0nic.org.ua/static/books/python/) before its gone

strong warez abilities lol

---

### Post by pmasiar on 2008-07-17
Another vote for ElementTree. It's so good it was included in core libraries (since 2.5).

Compared to SAX or DOM, which are very static-language oriented, ET builds dictionary of dictionaries with elements and attributes - much simpler to comprehend and use than any of the "standard" solutions.

---

### Post by Wybiral on 2008-07-17
> **LaRoza said:**
> Use the DOM because it is the most standard way...

Standard, for other languages, but for Python ElementTree is much more commonly used these days.

---

### Post by ghostdog74 on 2008-07-17
> **babacan said:**
> strong warez abilities lol

just simple google search. Nothing fancy.

---

### Post by LaRoza on 2008-07-17
> **Wybiral said:**
> Standard, for other languages, but for Python ElementTree is much more commonly used these days.

I was merely pointing out there is no single "better" option.

I use the DOM because it is included in ECMA-262 R2, and I use that a lot.

---

### Post by xelapond on 2008-07-17
Another vote for ElementTree.  I needed a fast way to parse xml, and I was able to figure out a good amount of it in about 10 minutes.  Its really simple, but very powerful at the same time(like Python!)

All the best, 

Alex

---

### Post by Wybiral on 2008-07-17
> **LaRoza said:**
> I was merely pointing out there is no single "better" option.

I use the DOM because it is included in ECMA-262 R2, and I use that a lot.

But the OP was asking about Python, and the Python idiom is to use ElementTree instead of the DOM module... It's just more common and Pythonic (not to mention more convenient). And if it's HTML instead of standard XML, the best to use is BeautifulSoup. And yes, it is "better" than the other XML parsers (for parsing HTML) and provides an ElementTree-like interface.

---

### Post by LaRoza on 2008-07-17
> **Wybiral said:**
> But the OP was asking about Python, and the Python idiom is to use ElementTree instead of the DOM module... It's just more common and Pythonic (not to mention more convenient). And if it's HTML instead of standard XML, the best to use is BeautifulSoup. And yes, it is "better" than the other XML parsers (for parsing HTML) and provides an ElementTree-like interface.

I know... I said that is why I used it ;)

The DOM isn't hard to use, so these other options must be extremely easy to use.

---

