---
title: "I need help with my shell script"
date: 2010-07-05
forum: Programming Talk
---

### Post by hoboy on 2010-07-05
I have xml file, like file.xml.
wich contains elements like this:
<rewriteURI uriStartString="../types" rewritePrefix="C:\Documents and Settings\zzz\Desktop\test\types" />.
an example of how the xsd file is.
<xs:include schemaLocation="../types/test.xsd"/>.
What I want is.
If XMLSpy (or another program validates the  test.xsd) that use file.xml,it wil look for Test.xsd in C:\Documents and Settings\zzz\Desktop\test\types\test.xsd folder.
Question: is this probleme better to solve with shell script ?
The solution I want to implements.
1.I read file.xml
     one element at time.
  when i find <rewriteURI uriStartString="../types" rewritePrefix="C:\Documents and Settings\zzz\Desktop\test\types" />.
2. I will read the path toC:\Documents and Settings\zzz\Desktop\test\types to make sure that text.xsd exist.
is this posible shell script ?

---

