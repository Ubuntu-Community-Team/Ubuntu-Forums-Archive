---
title: "SAX document parsing"
date: 2008-02-08
forum: Programming Talk
---

### Post by river22_34 on 2008-02-08
Hi everyone,
                     In my interview I said in DOM parser we load the whole document before manipulating it while in SAX parser we don't need to load the whole document.

The interviewer started asking me if in SAX parser, we need to load atleast little bit in order to manipulate? What could be the answer to this ? 

Also I have put up a poll on this question. Please cast your votes & your comments regarding this topic. Thank you.

---

### Post by popch on 2008-02-09
DOM (Document Object Model works by converting a serial text which describes a hierarchically organised document into a hierarchy of nodes representing the same document.

Hence, you can expect a DOM parser to load and restitute an entire document which your application then proceeds to process. 

This is clearly shown by the vocabulary used by DOM: this node, this node's properties, the parent node of this node, the left and right siblings, and so on.

SAX, on the other hand, is about 'events' a DOM parser would encounter if a DOM parser was used to parse a particular document. 

The vocabulary of a SAX parser expresses this clearly: Element begins, element ends, element attribute found,  element content found and so on.

Thus, a SAX parser need not process all of an XML document in order to be useful. An application using a SAX parser need not store even the smallest fraction of the part of the document which is actually read.

It would be perfectly possible (and also simple) to write a program which determines the average number of attributes elements have in a given document, or the average length of attribute values, or the most frequently occurring data value in attributes with names starting with 'co', and so on.

You can certainly stop processing an XML document at any place within the document, once your application has met its objectives. You can also start reading an XML document in the middle, provided your application can use the partial result yielded by such an operation.

You can also write a rather simple program which uses SAX to construct the same graph of nodes that DOM would.

---

### Post by Shin_Gouki2501 on 2008-02-09
If u go deeper in this its certainly becomes interesting. Following concepts :
1. Access Control ( random or sequential)
2.  Flow Control ( Push or Pull )
3. Tree management (hierarchical or nested)

If u can assign those clearly to DOM , SAX and e.g. Pull Parser like Java Stax. Then u got through it ;)

[http://lists.xml.org/archives/xml-dev/200201/msg01633.html](http://lists.xml.org/archives/xml-dev/200201/msg01633.html)

---

