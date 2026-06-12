---
title: "HSQLDB2.0 and Python programming"
date: 2011-10-26
forum: Programming Talk
---

### Post by zhaotianwu on 2011-10-26
I'm learning Python programming and designing a medicine tracking database. Currently I'm using LibreOffice Base to build the database. Eventually, however, I'm going to build my own application GUI using Python to deal with the data. LibO Base uses HSQLDB by default. I was wondering if in the future I need to migrate to my own Python application, is it a better idea to start using SQLITE from the beginning, or is it better to stick with HSQLDB and everything will be just as fine? Any comment will be appreciated. Thanks.

---

### Post by karlson on 2011-10-27
> **zhaotianwu said:**
> I'm learning Python programming and designing a medicine tracking database. Currently I'm using LibreOffice Base to build the database. Eventually, however, I'm going to build my own application GUI using Python to deal with the data. LibO Base uses HSQLDB by default. I was wondering if in the future I need to migrate to my own Python application, is it a better idea to start using SQLITE from the beginning, or is it better to stick with HSQLDB and everything will be just as fine? Any comment will be appreciated. Thanks.

I would suggest using MySQL or PostgreSQL.  I think that your application once you get it going would require a database that would require access by multiple users.

---

### Post by zhaotianwu on 2011-10-27
> **karlson said:**
> I would suggest using MySQL or PostgreSQL.  I think that your application once you get it going would require a database that would require access by multiple users.

 No, multiple-user is not an issue at all. This application is only for family use and we only have one person who is good at typing.  Is HSQLDB generally friendly towards Python and Ubuntu?

---

### Post by The Cog on 2011-10-28
I could be wrong, but I thought that hsqldb was implemented in java. I would not think that's a good match for a python app. On that basis, I would suggest using sqlite, which does play nice with python - I use apsw to access sqlite databases on a regular basis. For a single-user app, I wouldn't go to the overkill of MySQL or PostgreSQL.

Sqlite doesn't come with a GUI. The best GUI I have seen is a plug-in for firefox called sqlite-manager.

---

### Post by gsmanners on 2011-10-28
Probably the main advantage for using sqlite with Python would be its convenient [documentation]("http://docs.python.org/library/sqlite3.html").

---

### Post by zhaotianwu on 2011-10-28
> **The Cog said:**
> I could be wrong, but I thought that hsqldb was implemented in java. I would not think that's a good match for a python app. On that basis, I would suggest using sqlite, which does play nice with python - I use apsw to access sqlite databases on a regular basis. For a single-user app, I wouldn't go to the overkill of MySQL or PostgreSQL.

Sqlite doesn't come with a GUI. The best GUI I have seen is a plug-in for firefox called sqlite-manager.

 Hey The Cog, thank you for the tip. The problem that I'm facing is, I also want to make good use of LibO Base at this moment, then progress into my own Python application. Now it seems that I'm facing a dilemma, Base or Python (HSQLDB or SQLITE). Is this a real dilemma in your opinion? Or it is just a beginner's dilemma?

---

### Post by The Cog on 2011-10-29
I don't think it's really a dilemma. It shouldn't be hard to transfer the data from the LibO database to sqlite when the time comes. I'm sure sqlite can import csv data, and you should be able to read the LibO tables in calc and export them to csv.

I really wish you could get Libo Base to use sqlite instead of that oddball java database.

---

### Post by memilanuk on 2011-10-29
Looks like Libre Office Base may be moving to SQLite at some point in the future anyways...

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=13&t=40525](http://user.services.openoffice.org/en/forum/viewtopic.php?f=13&t=40525)

---

