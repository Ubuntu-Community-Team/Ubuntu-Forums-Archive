---
title: "Html &amp; xml"
date: 2009-08-14
forum: Programming Talk
---

### Post by nebu on 2009-08-14
I want to store some html document code in a xml file

how do i do this

the xml is taking the html tags to be xml tags and hence the whole things is oging haywire

---

### Post by Arndt on 2009-08-14
> **nebu said:**
> I want to store some html document code in a xml file

how do i do this

the xml is taking the html tags to be xml tags and hence the whole things is oging haywire

Something which works as HTML while conforming to XML is called XHTML. Here is an on-line converter: [http://www.cruto.com/resources/code-generators/code-converters/html-to-xhtml.asp](http://www.cruto.com/resources/code-generators/code-converters/html-to-xhtml.asp)

---

### Post by hessiess on 2009-08-14
> **nebu said:**
> I want to store some html document code in a xml file

how do i do this

the xml is taking the html tags to be xml tags and hence the whole things is oging haywire

You need to replace the "<" and ">" characters with something else, the common HTML representation being "&lt;" and "&gt;", then convert it back when you read the XML file.

---

### Post by Occasionally Correct on 2009-08-14
It sounds like you want to use [CDATA]("http://en.wikipedia.org/wiki/CDATA"):

```
<?xml version="1.0" encoding='ISO-8859-1'?>

<some-structure>
    <some-data>
        <![CDATA[
        <p>HTML!</p>
        ]]>
    </some-data>
</some-structure>
```

---

