---
title: "Python + UNOIDL + Packages import"
date: 2009-09-02
forum: Programming Talk
---

### Post by alkatron on 2009-09-02
I'm a python newbie with

> 
Linux gino-desktop 2.6.24-24-generic #1 SMP Tue Jun 30 19:54:36 UTC 2009 x86_64 GNU/Linux
python 2.5.2
eclipse build:20090619-0625 + pydev


and i'm trying to run an example found on linux-journal....

[http://www.linuxjournal.com/content/starting-stopping-and-connecting-openoffice-python]("http://www.linuxjournal.com/content/starting-stopping-and-connecting-openoffice-python")

I get an "unresolved import" error (in the ide) and a "importerror:cannot import Propertyvalue" runtime-error on this line

```
from com.sun.star.beans import PropertyValue

```
I searched by google and found that i have to generate Source Code from UNOIDL Definitions as in 

[http://wiki.services.openoffice.org/wiki/Documentation/DevGuide/WritingUNO/Generating_Source_Code_from_UNOIDL_Definitions]("http://wiki.services.openoffice.org/wiki/Documentation/DevGuide/WritingUNO/Generating_Source_Code_from_UNOIDL_Definitions")

I have done it and generated com/sun/star/beans/PropertyValue.hdl and hpp
I tried also to copy them almost everywhere
but the error is still there.....

Where am I wrong or what is still missing?

Thanks to everyone...an sorry for my english

---

