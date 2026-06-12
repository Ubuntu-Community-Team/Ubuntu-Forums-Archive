---
title: "Need XSD creating tool for Ubuntu 9.04"
date: 2009-07-21
forum: Programming Talk
---

### Post by venkyms on 2009-07-21
Hi Friends,

Is there any tool to create .xsd schema file from the given .xml file, please let me know if any

Thanks
Venkat

---

### Post by jero3n on 2009-07-21
You can write a small program in C# to load the xml into a dataset and then save the schema to xsd with DataSet.WriteXmlSchema method.

Does this suit you? Do you need source code?

---

### Post by Reiger on 2009-07-21
IDE's tend to have (hidden) tools for this kind of job.

---

### Post by Shin_Gouki2501 on 2009-07-21
java(5 , better 6) got tools for generating xmlschema from a java class, look in java/bin
for 'schemagen'
and try to work with the necessary parameters.

see here and google for more info :
[http://docs.sun.com/app/docs/doc/819-3662/schemagen-1m?a=view](http://docs.sun.com/app/docs/doc/819-3662/schemagen-1m?a=view)

---

