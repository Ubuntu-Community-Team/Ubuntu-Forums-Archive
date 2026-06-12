---
title: "Desktop Database Cross Platform?"
date: 2007-01-15
forum: Programming Talk
---

### Post by gareththegeek on 2007-01-15
What is a good replacement for ms access in linux for crossplatform development...

I have decided to try and write a game recently which will require a database.  Since the game doesn't have to be great performance-wise I decided to use C# to speed up development.  I started writing the thing in Windows since that was on the computer I was at at the time and so used Access as the database.  But since my main pc has ubuntu I would like to make the app work through mono on linux too.

So what I want is a replacement for MS Access that will work in both windows and linux, is based on a file which can be moved about (e.g. .mdb files), and that will work through ADO.NET (OleDb/ODBC etc).  Know you of such a db?

Any suggestions much appreciated!

G!

---

### Post by Tomosaur on 2007-01-15
> **gareththegeek said:**
> What is a good replacement for ms access in linux for crossplatform development...

I have decided to try and write a game recently which will require a database.  Since the game doesn't have to be great performance-wise I decided to use C# to speed up development.  I started writing the thing in Windows since that was on the computer I was at at the time and so used Access as the database.  But since my main pc has ubuntu I would like to make the app work through mono on linux too.

So what I want is a replacement for MS Access that will work in both windows and linux, is based on a file which can be moved about (e.g. .mdb files), and that will work through ADO.NET (OleDb/ODBC etc).  Know you of such a db?

Any suggestions much appreciated!

G!

I doubt MS Access is the right tool for the job then, if you want cross-platform capability. You may be better off using something like postgresql or mysql. There are frontends for both which make database design etc easier, but if you know SQL, it's often faster (and easier to incorporate into other software). Both are available on linux and windows:
[Postgresql](http://www.postgresql.org/)
[MySQL](http://www.mysql.com/)

I personally prefer postgresql, but they're pretty similar.

As for the ADO.NET thing, I don't know much about support for that, sorry. Since it's .NET, you may well be tied to Windows if you stick with it, unless you can find something in Mono to handle it all.

---

### Post by eteran on 2007-01-15
Take a look at [SQlite](http://www.sqlite.org).

---

### Post by gareththegeek on 2007-01-15
Thanks!

MySQL and Postgresql look a bit heavy duty for this job but SQLite looks like exactly what I need.  When u combine it with this fella [http://thirstycrow.net/blog/archive/2006/03/17/939.aspx]("http://thirstycrow.net/blog/archive/2006/03/17/939.aspx") you've also got ado.net support, a gui and a tutorial :D

G!

---

### Post by pmasiar on 2007-01-15
for web-based application python+SQLite is very agile - if you don't need multiuser abilities of MySQL and other "real" databases. For desktop, there are [Kexi]("http://en.wikipedia.org/wiki/Kexi") and [Base]("http://en.wikipedia.org/wiki/OpenOffice.org_Base") (for KOffice and OpenOffice resp).

---

### Post by Daverz on 2007-01-15
You might also take a look at [http://dabodev.com](http://dabodev.com)

---

