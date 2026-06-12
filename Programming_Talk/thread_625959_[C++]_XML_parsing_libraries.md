---
title: "[C++] XML parsing libraries"
date: 2007-11-28
forum: Programming Talk
---

### Post by iharrold on 2007-11-28
Anyone know of any good XML parsing libraries?  I.e., I load up a XML schema then load an xml file that uses the schema and I can pull relevant data from the file...

If I don't have to code up the text parser for both the schema and xml file readers that would be great...

---

### Post by leg on 2007-11-28
[TinyXML]("http://www.grinninglizard.com/tinyxml/") is pretty nice.

---

### Post by Vadi on 2007-11-28
I think the first entry here will do well? ([click]("http://sourceforge.net/search/?type_of_search=soft&type_of_search=soft&words=c%2B%2B+xml+parse"))

---

### Post by aks44 on 2007-11-28
[Apache Xerces-C++]("http://xerces.apache.org/xerces-c/") (formerly an IBM DeveloperWorks product) is IMHO the reference implementation. It has both SAX and DOM parsers.

I'd recommend building it together with [ICU]("http://xerces.apache.org/xerces-c/build-misc.html#ICUPerl") (IBM's International Components for Unicode) for the best support of character encodings.

EDIT: FWIW it is in Ubuntu's repositories, and already built together with ICU, just waiting to be linked to... And I wonder why I love Linux... :D

---

### Post by iharrold on 2007-11-28
Thanks everyone... 

By chance anyone know if there a .deb package for TinyXML?

I looked around with:
```
sudo aptitude search tiny*
sudo aptitude search ticpp*
```

and some googling... no luck.

Edit::
I just downloaded the gz then unzipped it and added it to my project as an external resource.  Then compiled it.

---

