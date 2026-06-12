---
title: "Suggest an XML/DTD verifier for Linux?"
date: 2007-09-04
forum: Programming Talk
---

### Post by marx2k on 2007-09-04
I currently have a class where I am writing XML and DTD schemas and I am looking for a standalone program that will run through my schemas and verify them or give detailed error reports?

I have 2 plugins for Firefox but they are a bit convoluted.

I am using the XML Developer Toolbar as well as Total Validator 4.2

Does anyone have any other suggestions?

---

### Post by Mr_Smiley on 2007-09-05
I have found [XML Copy Editor]("http://xml-copy-editor.sourceforge.net/") useful.

---

### Post by AZzKikR on 2007-09-05
Why DTD and not XSD?

---

### Post by marx2k on 2007-09-06
Perhaps I don't fully understand the difference between the two yet.  I am currently doing simple XML and DTD writeups and just want to find something that will verify that the DTD I am writing that defines the XML within the document is valid.  I will try using the suggested solution.

---

### Post by marx2k on 2007-09-06
Followup: This is EXACTLY what I was looking for and MORE.  Thank you very much for the suggestion!

---

### Post by Mr_Smiley on 2007-09-06
> **marx2k said:**
> Followup: This is EXACTLY what I was looking for and MORE.  Thank you very much for the suggestion!
Not a problem. I was looking for the same sort of thing not that long ago.

---

### Post by AZzKikR on 2007-09-07
> **marx2k said:**
> Perhaps I don't fully understand the difference between the two yet.  I am currently doing simple XML and DTD writeups and just want to find something that will verify that the DTD I am writing that defines the XML within the document is valid.  I will try using the suggested solution.

DTD is older and in my opinion, obsolete. XML Schema (XSD) can do anything DTD can, and even more. A summary of DTD vs XSD:

DTD:
[LIST]
[*]Is old, and derived from SGML;
[*]No support of new XML features. Most important is namespaces. If you are going to work with XML, SOAP and that sort of things, namespaces are very important;
[*]DTD uses a non-XML syntax;
[*]Therefore, DTD is not very easy to understand IMHO.
[/LIST]

XSD:
[LIST]
[*]Is new;
[*]Support fore namespaces;
[*]Uses XML syntax, and therefore easier to extend, and understand;
[*]Has better support for datatypes;
[*]Can include regular expressions for validating XML attribute-values or node-values;
[*]Has recommendation status from W3C.
[/LIST]

---

### Post by LaRoza on 2007-09-07
In XSD, you get phrases like this, quoted from my book:

> 
The element element defines an element.


Which is true, but how does one explain THAT.

---

### Post by cwaldbieser on 2007-09-08
> **AZzKikR said:**
> DTD is older and in my opinion, obsolete. XML Schema (XSD) can do anything DTD can, and even more. A summary of DTD vs XSD:

DTD:
[LIST]
[*]Is old, and derived from SGML;
[*]No support of new XML features. Most important is namespaces. If you are going to work with XML, SOAP and that sort of things, namespaces are very important;
[*]DTD uses a non-XML syntax;
[*]Therefore, DTD is not very easy to understand IMHO.
[/LIST]

XSD:
[LIST]
[*]Is new;
[*]Support fore namespaces;
[*]Uses XML syntax, and therefore easier to extend, and understand;
[*]Has better support for datatypes;
[*]Can include regular expressions for validating XML attribute-values or node-values;
[*]Has recommendation status from W3C.
[/LIST]

I always liked schematron [http://www.schematron.com/overview.html]("http://www.schematron.com/overview.html")
I found it to be a easier to use when describing some things that were hard to express in XSD.

---

