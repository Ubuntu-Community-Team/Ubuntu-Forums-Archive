---
title: "Can't get a catalog to co-operate in docbook"
date: 2009-11-28
forum: Programming Talk
---

### Post by YourSurrogateGod on 2009-11-28
Hey guys,

I'm kind of stuck here.  I was looking at [this](http://opensource.bureau-cornavin.com/crash-course/en/formal-public-ids.html) tutorial as a rough guide on working with docbook (yes I know there's an O'Reilly book, but first I want to get my feet wet since this is my first time and all).  Now, I got to the part about the catalog.  It makes sense, instead of changing *every* instance of the included file, you just have a central area that needs to be changed once.  However, I'm having a hard time trying to actually getting to work, as the below console output shows :) .  What am I doing wrong?

test.xml
```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE book PUBLIC "-//OASIS//DTD DocBook XML V4.4//EN" 
          "http://nwalsh.com/docbook/xml/3.1.4/db3xml.dtd" [
<!--  <!ENTITY introduction SYSTEM "introduction.xml">
  <!ENTITY marketing SYSTEM "marketing-plan.docbook">
  <!ENTITY advertising SYSTEM "advertising-campain.docbook">
  <!ENTITY conclusion SYSTEM "foo/conclusion.xml"> -->
  <!ENTITY cereals "<productname>Frobozz Cerals</productname>">
  <!ENTITY orange-juice "<productname>Hourmade Orange Juice</productname>">
]>
<book id="marketing-study" lang="en">
  <bookinfo>
    <title>
      Marketing study about &cereals;
    </title>
  </bookinfo>
  &introduction;
<!--  &marketing;
  &advertising; -->
  &conclusion;
</book>

```
introduction.xml
```
<appendix id="licence">
  <title>
    Licence
  </title>
  <para>
    This document is released under Free Documentation licence; the terms of
    this licence are detailed below.
  </para>
  <sect1>
    <title>
      Free Documentation Licence
    </title>
    <para>
      blah
    </para>
  </sect1>
</appendix>
```
conclusion.xml
```
<appendix id="conclusion">
  <title>
    Conclusion
  </title>
  <para>
    And that's what it's all about!
  </para>
  <sect1>
    <title>
      Yay!
    </title>
    <para>
      blah
    </para>
  </sect1>
</appendix>

```
catalog
```
<?xml version="1.0"?>
<!DOCTYPE catalog
   PUBLIC "-//OASIS/DTD Entity Resolution XML Catalog V1.0//EN"
   "http://www.oasis-open.org/committees/entity/release/1.0/catalog.dtd">
<catalog xmlns="urn:oasis:names:tc:entity:xmlns:xml:catalog">
  <group prefer="public" xml:base="file:///usr/share/xml/">
    <public publicId="-//OASIS//Introduction//EN"
       uri="introduction.dtd"/>
<!--    <system systemId="http://www.oasis-open.org/docbook/xml/4.5/docbookx.dtd"
       uri="docbook45/docbookx.dtd"/>
    <system systemId="docbook4.5.dtd"
       uri="docbook45/docbookx.dtd"/> -->
  </group>
</catalog>

```

Output at console:
```
$ docbook2pdf test.xml 
Using catalogs: /etc/sgml/catalog
Using stylesheet: /usr/share/docbook-utils/docbook-utils.dsl#print
Working on: /home/ysg/Desktop/Documents/Programming/docbook/test/test.xml
openjade:/home/ysg/Desktop/Documents/Programming/docbook/test/catalog:3:62:E: name expected
openjade:/home/ysg/Desktop/Documents/Programming/docbook/test/catalog:15:1:E: end of entity in comment
openjade:/home/ysg/Desktop/Documents/Programming/docbook/test/catalog:3:3:E: cannot find "PUBLIC"; tried "/home/ysg/Desktop/Documents/Programming/docbook/test/PUBLIC", "/usr/local/share/sgml/PUBLIC", "/usr/share/sgml/PUBLIC"
openjade:/home/ysg/Desktop/Documents/Programming/docbook/test/test.xml:17:3:W: cannot generate system identifier for general entity "introduction"
openjade:/home/ysg/Desktop/Documents/Programming/docbook/test/test.xml:17:3:E: general entity "introduction" not defined and no default entity
openjade:/home/ysg/Desktop/Documents/Programming/docbook/test/test.xml:17:15:E: reference to entity "introduction" for which no system identifier could be generated
openjade:/home/ysg/Desktop/Documents/Programming/docbook/test/test.xml:17:2: entity was defined here
openjade:/home/ysg/Desktop/Documents/Programming/docbook/test/test.xml:20:3:W: cannot generate system identifier for general entity "conclusion"
openjade:/home/ysg/Desktop/Documents/Programming/docbook/test/test.xml:20:3:E: general entity "conclusion" not defined and no default entity
openjade:/home/ysg/Desktop/Documents/Programming/docbook/test/test.xml:20:13:E: reference to entity "conclusion" for which no system identifier could be generated
openjade:/home/ysg/Desktop/Documents/Programming/docbook/test/test.xml:20:2: entity was defined here

```

---

