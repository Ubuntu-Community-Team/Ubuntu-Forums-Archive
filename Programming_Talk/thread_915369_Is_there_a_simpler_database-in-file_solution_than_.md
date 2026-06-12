---
title: "Is there a simpler database-in-file solution than SQL Lite?"
date: 2008-09-09
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-09-09
Is there something similar to SQLLite which can be accessed through C++ code (like SQL Lite), but as easy to configure as an spread sheet?  I thought about using .csv files and parsing the text, but I would like to keep all tables bundled in one file.  Is a free interface to open and read Excel files through C++ calls?

---

### Post by stevescripts on 2008-09-09
Are you needing to do something with Excel files that Open Office doesn't handle?

SQLite can import csv files, also.

Steve

---

### Post by cb951303 on 2008-09-10
sqllite is as simple as you will get :)

---

### Post by themusicwave on 2008-09-10
There is an Open Office API to read and write to excel and open document spreadsheets.

However, I would not call it easy to use.  I've also only used it with Java, but it says it works from C++ as well.

[http://api.openoffice.org/]("http://api.openoffice.org/")

I think you really want a database like SQLite though.

---

### Post by pmasiar on 2008-09-10
there are BDM and shelf, but SQLite is as easy **SQL** database as you can get. Meaning, if SQLIte is not enough, you can trivially upgrade to more powerful DB, like MySQL or Postgress. No other options mentioned above don't have that, IMHO rather important 'fallback' capacity.

---

