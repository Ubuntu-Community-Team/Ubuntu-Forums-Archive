---
title: "Debugging XML &amp; XSL sites"
date: 2010-02-24
forum: Programming Talk
---

### Post by ZuLuuuuuu on 2010-02-24
Hello,

Recently I'm trying to learn how to create web sites using XML & XSL & XPath. But there is a big problem I'm facing: whenever there is an error the web site goes completely blank and it usually does not show any error. It shows, for example, tags left open. But, for example, when I write {mytag} instead of @mytag then it does not show any errors though the page still goes completely blank. How can I debug this kind of errors?

---

### Post by Zugzwang on 2010-02-24
Did you try using an XSLT processor like "xsltproc" from the terminal? It might give you more detailled error messages.

---

### Post by Reiger on 2010-02-24
Unit testing. Split up your XSLT file in multiple smaller ones, create dummy XML documents and stress test your algorithm so it behaves as expected in all cases.

If you have PHP set up (with XSL module activated) you can use PHP to create a page to test XML against XSLT depending on, say, GET query string. This has the added benefit of the fact that any warnings and errors written to STDOUT will find their way to your screen through PHP warnings.

---

