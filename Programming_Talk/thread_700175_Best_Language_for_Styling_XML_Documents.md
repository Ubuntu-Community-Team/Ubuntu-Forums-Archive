---
title: "Best Language for Styling XML Documents"
date: 2008-02-18
forum: Programming Talk
---

### Post by TreeFinger on 2008-02-18
What is the best way to style an XML document?

---

### Post by LaRoza on 2008-02-18
In what context? CSS for the web, XSL can be used as well.

---

### Post by TreeFinger on 2008-02-18
> **LaRoza said:**
> In what context? CSS for the web, XSL can be used as well.

I don't understand your first question about what context.

Currently I am trying to style an XML document with CSS but it seems like I can't do as much as I would like to.

---

### Post by LaRoza on 2008-02-18
For XML, you have to remember that there are no defaults, so you have to specify how it is to be displayed.

---

### Post by a9bejo on 2008-02-18
> **TreeFinger said:**
> I don't understand your first question about what context.

XML is a way to add structure to data so it can be processed by machines.    It was not made to be read by humans, so it makes usually no sense to "style" it for humans. 

You can, however, use a program to process a XML Document and create something that can be presented to users.  For example, a web browser can transform a XHTML document into a visual picture of a web page, or a Jabber client transforms a XMPP message into a text that can be read in a instant messaging client.  XHTML and XMPP are both data formats based on XML.  So if you say you want to "style XML", it is important to know what kind of document you want to process for what kind of program.

Some web browsers can also transform arbitrary xml to HTML on the fly, and some of them even understand CSS stylesheets that are attached to the data.  However, If you have data in a XML Document, and you want to visualize that data in a browser, you should transform that data to XHTML.

While pretty much any programming language can be used to process XML, XSLT was made exactly for this task, and it has the advantage that it is a popular standard, which means you can use XSLT from most  software platforms/languages.  On the other hand, XSLT programs are itself XML documents, which makes the source code a bit bulky.

---

### Post by pmasiar on 2008-02-18
... and makes XSLT rather hard to read, as XSLT source code is XML, and the code snippets generated are also XML.

---

### Post by popch on 2008-02-18
> **pmasiar said:**
> ... and makes XSLT rather hard to read, as XSLT source code is XML...

.. which is, however, strictly a matter of opinion, since some people are quite comfortable reading XML and XSLT.

XSLT is XML, therefore you can also use XSLT to 'style' and otherwise process XSLT files.

---

### Post by TreeFinger on 2008-02-18
Thanks for the replies. The reason I ask this question is because I am working on a project and we are asked to design an XML document, create the DTD, and then add style to the document with CSS. 

It seems like I'll just be changing text size and color.. maybe adding some backgrounds and borders.

---

