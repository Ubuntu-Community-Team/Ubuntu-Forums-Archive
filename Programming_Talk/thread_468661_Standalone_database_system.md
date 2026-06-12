---
title: "Standalone database system"
date: 2007-06-09
forum: Programming Talk
---

### Post by joeljkp on 2007-06-09
I'm looking for a way to create a standalone personal database that I can easily send to people without having to reside on a server or anything, like MS Access or OpenOffice Base.

The default choice seems to be Access, even though I would need to use Windows (or WINE). In my project it would be inappropriate to expect people to download OpenOffice just to view my database.

Are there any other choices, or am I stuck with Access?

---

### Post by keithweddell on 2007-06-09
You should be able to do this with sqlite.  Not sure how you get others to install the sqlite engine though.  It might be possible to embed it in an application.


Keith

---

### Post by Max_Might on 2007-06-09
SQLITE is very nice, I am using it too :) you should try it.

---

### Post by Catsworth on 2007-06-09
I'm having problems finding a similar solution, I think the OP wants a database that carries its own files with it and doesn't necessarily require any installation on the part of the user.

---

### Post by pmasiar on 2007-06-09
> **joeljkp said:**
> I'm looking for a way to create a standalone personal database that I can easily send to people without having to reside on a server or anything, like MS Access or OpenOffice Base.

Not sure what you mean. SQLite is *simpler* than Access: smaller footprint, simpler management (it's a single-user database after all). Of course it needs to be installed on every computer which will use it, but it is no different from Access.

> The default choice seems to be Access, even though I would need to use Windows (or WINE). In my project it would be inappropriate to expect people to download OpenOffice just to view my database.

But if your "people" don't have MS Office, how they will use your database? You don't care about Linux users?

---

### Post by joeljkp on 2007-06-09
Thanks for the feedback. The underlying assumption (which happens to be valid) is that everyone I'm working with already has Office installed.

SQLite is interesting... but to distribute it so that others can use it, I would need to code it up, embed the db, and create a whole GUI, etc. for it, right?

---

### Post by AnRa on 2007-06-09
You can use SQLite and distribute your DB with any of these tools: [http://www.sqlite.org/cvstrac/wiki?p=ManagementTools](http://www.sqlite.org/cvstrac/wiki?p=ManagementTools)

---

### Post by pmasiar on 2007-06-09
> **joeljkp said:**
> The underlying assumption (which happens to be valid) is that everyone I'm working with already has Office installed.

then why you need wine? *You* want to develop on Linux, and your users will use it on Windows?

> SQLite is interesting... but to distribute it so that others can use it, I would need to code it up, embed the db,


SQLite is separate install (is not "embedded" in your database -- db is just data. But installing SQLite can be part of your app install package. 

>  and create a whole GUI, etc. for it, right?

Yes. If you want GUI frontend, someone need to create it. ;-)

If you want to develop under Linux, and your users run Windows, you have two options:
- switch to windows like your users and develop in Access/VB or whatever -- including new IronPython for .NET
- use cross-platform solution, like wx for GUI and SQLite for database, or whatever Mono world provides. Python is also decent cross-platform language, with wxPython and pySQLite.

Depends what skills you have now, and what you want to learn from this project.

---

### Post by joeljkp on 2007-06-13
I'm beginning to think there's a missing niche here: a user-friendly database access program generator, similar to OOo Base or MS Access, but that would allow you to generate a standalone .exe containing all your pretty forms and reporting tools, etc. Such a thing would let you design db interfaces without having to learn GUI programming, but would let you simply bundle an executable with your database instead of requiring that everyone has a certain package already installed.

---

### Post by pmasiar on 2007-06-13
like [Base](http://en.wikipedia.org/wiki/OpenOffice.org_Base) or [kexi](http://en.wikipedia.org/wiki/Kexi)?

---

### Post by joeljkp on 2007-06-13
> **pmasiar said:**
> like [Base](http://en.wikipedia.org/wiki/OpenOffice.org_Base) or [kexi](http://en.wikipedia.org/wiki/Kexi)?

Can those create standalone executables so that users without Base or Kexi installed can use the database and all its associated forms, reports, etc.?

---

### Post by kknd on 2007-06-13
Sqlite does the job. For Java, thre is Derby, HSQLDB, Neodatis (OO) and more.

---

### Post by mlaitinen on 2012-11-15
Sorry to wake up such an old thread..

Apparently nobody was able to answer the original question. I'm now facing the same problem.

I don't have MS Access nor do I want to buy it. Some of the users I'm developing the application to have it, some don't. Would be nice to see a solution with similar features than Access (relations, grid editor, views) but without the need to have a separate viewer software installed.

---

### Post by ofnuts on 2012-11-15
There is a Firefox extension to browse/manage SQLite databases. Pretty cool stuff.

---

### Post by slickymaster on 2012-11-16
I'll recommend you Apache Derby. It's an open source relational database implemented entirely in Java.~

It has a small footprint -- about 2.6 megabytes for the base engine and embedded JDBC driver, it's based on the Java, JDBC, and SQL standards.
The embedded JDBC driver lets you embed Derby in any Java-based solution.

Here's the [link]("http://db.apache.org/derby/").

---

### Post by wildmanne39 on 2012-11-16
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

