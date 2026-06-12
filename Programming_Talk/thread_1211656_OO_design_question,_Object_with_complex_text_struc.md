---
title: "OO design question, Object with complex text structure"
date: 2009-07-12
forum: Programming Talk
---

### Post by badperson on 2009-07-12
Hi,
I have a field in an object that is structured text; It has headings and paragraphs, you can have any number of headings and paras in any order. 

For the time being, I decided to have the datatype for that field be a dom4j xml node, because I wasn't sure how to create an object with string fields that would account for the different elements and a different order...I suppose you could have a TextEntry class with a type and text fields, and the object I'm writing could have an arrayList of TextEntry objects, that could work...since the app uses xml anyway, I thought it would make life easier just to use that format...

any ideas? 
bp

---

### Post by dwhitney67 on 2009-07-13
What you describe seems fine to me... a structure that defines the TextEntry (text content and type), and then an array, say TextEntryArray, of these TextEntry object(s).

The TextEntryArray should ensure that you can add new TextEntry objects to the end, and also ensure that all of your TextEntry objects are maintained in order of creation.

P.S.  It is probably better to use a "List", rather than an "Array"; I think you mentioned this too.

---

