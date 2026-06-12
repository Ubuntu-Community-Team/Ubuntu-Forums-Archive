---
title: "Viewing an Access 2000 database"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by lilmentor on 2008-05-13
I would like to switch to Ubuntu but I need one thing that is important to my work.

I have an Access 2000 file format .mlb that I access using Access 2007 and would like to view/edit this database under a Ubuntu environment. Does anyone have experience with this?

---

### Post by dRock1286 on 2008-05-13
Have you tried OpenOffice?

---

### Post by lilmentor on 2008-05-13
> **dRock1286 said:**
> Have you tried OpenOffice?

No.

---

### Post by dRock1286 on 2008-05-13
Give it a shot.  Its able to read almost all of MS's file formats and save to them as well.  OOo 3 will even be able to do MS's new .~~~x formats...

---

### Post by aeiah on 2008-05-13
as far as i know, openoffice can handle access databases. id be careful though, because you may find that once you get back to work, no one will be able to open the access database without a copy of open office. test it a bit first hehe

---

### Post by Monicker on 2008-05-13
> **lilmentor said:**
> I would like to switch to Ubuntu but I need one thing that is important to my work.

I have an Access 2000 file format .mlb that I access using Access 2007 and would like to view/edit this database under a Ubuntu environment. Does anyone have experience with this?

These may help you:

[http://wiki.services.openoffice.org/wiki/Connecting_to_Microsoft_Access]("http://wiki.services.openoffice.org/wiki/Connecting_to_Microsoft_Access")
[http://www.openoffice.org/FAQs/ms-access/ms-access.html]("http://www.openoffice.org/FAQs/ms-access/ms-access.html")

---

### Post by dRock1286 on 2008-05-13
As long as it is saved in the Microsoft format, MS Office will be able to open it.

---

### Post by lilmentor on 2008-05-13
Thanks, I will try it. (i will make a copy of the DB and try opening the copy.)

---

### Post by Go_Bucks on 2008-05-13
I work with Access databases and OpenOffice... do NOT try to work on an Access database from OpenOffice Base. The only thing you can do is CONNECT to the database and view/edit tables and queries. While that sounds great, none of the macros, relationships and higher level functionality of an Access database works in Base so you will more than likely mess up the whole database. Only work in Base if you intend to use the Access database as a back end and want to rebuild the front end in OpenOffice.

---

### Post by lilmentor on 2008-05-13
> **Go_Bucks said:**
> I work with Access databases and OpenOffice... do NOT try to work on an Access database from OpenOffice Base. The only thing you can do is CONNECT to the database and view/edit tables and queries. While that sounds great, none of the macros, relationships and higher level functionality of an Access database works in Base so you will more than likely mess up the whole database. Only work in Base if you intend to use the Access database as a back end and want to rebuild the front end in OpenOffice.

how about the forms?

---

### Post by Znort_Ubern00b on 2008-05-13
I have similar experience to Go_Bucks

couldn't use any forms when using Office Base only had tables etc so would not recommend OOo 2, not sure about 3 though might have better cross-platform functionality.

---

### Post by Go_Bucks on 2008-05-13
> **lilmentor said:**
> how about the forms?

You can not work on forms. The Access "database" is just the tables and queries. The other stuff, such as forms, use Microsoft-specific coding (VBA?) and is technically not part of the database itself.

Last I checked, the Linux ODBC driver or whatever other Linux driver you might use to connect to Jet databases can be kinda buggy as well. There are fewer problems using OOo in Windows, but even in Windows you still can't use forms. You can create new forms in Base, however.

I haven't had a chance yet to try Base in openoffice 3, though I have it installed. I work for a biological consulting firm and we use a central Access database to store all of our data. I want to port it over to Base so that we can have more computers available for data entry, but I have had issues with getting forms put together the way I want them (in 2.4 at least, putting together equivalent forms in Base requires more raw SQL knowledge than is necessary in Access, and I am not an expert on the subject by any means). 

I would also like to use Base because it is actually easier to generate reports that are editable in Microsoft Word than it is to do so from Access.

---

