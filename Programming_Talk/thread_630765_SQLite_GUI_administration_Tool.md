---
title: "SQLite GUI administration Tool"
date: 2007-12-03
forum: Programming Talk
---

### Post by kaervas59 on 2007-12-03
I'm looking for a SQLite database administration tool (GUI).

Do you have some recommendation?

---

### Post by pmasiar on 2007-12-03
I do not think SQLite has a GUI admin - it would not be lite, now would it? ;-)

To make your work with SQLite simpler, use ORM - object-relation mapper, like SQLObject or SQLAlchemy. It will generate getters/setters and searches from your DB structure.

Included in Turbogears :-)

---

### Post by Quikee on 2007-12-04
There is [sqlitebrowser]("http://sqlitebrowser.sourceforge.net/") (should be in the repository).. but it is not exactly a database administration tool. ;)

---

### Post by af20001 on 2007-12-04
There is a SQLite Manager Firefox extension available, I've started using it recently, seems to do everything I want. It's available from the main Firefox addons page.

---

### Post by kaervas59 on 2007-12-04
Great Thanks guys!

---

### Post by cdean on 2007-12-27
> **Quikee said:**
> There is [sqlitebrowser]("http://sqlitebrowser.sourceforge.net/") (should be in the repository).. but it is not exactly a database administration tool. ;)

It does not exist in the repositories.

RFP?

Really, though, the SQLite Manager extension for Firefox is 10x better and not Qt-based (not knocking Qt--XUL makes things look more uniform, IMO).

---

### Post by Quikee on 2007-12-28
> **cdean said:**
> It does not exist in the repositories.

It does exist in hardy's repository ([here]("http://packages.ubuntu.com/hardy/devel/sqlitebrowser")) - however I did not check the others. Sorry. ;)

> **cdean said:**
> Really, though, the SQLite Manager extension for Firefox is 10x better and not Qt-based (not knocking Qt--XUL makes things look more uniform, IMO).

Well sqlitebrowser suited my needs and I don't care about uniform look. Also I did not know about "SQLite Manager extension for Firefox" - I would not even in a dream go look for a database manipulation tool through plugins for a web browser. ;) However it looks decent - thanks.

---

### Post by airtonix on 2008-01-02
OK so im trying to find a dbase frontend like access that runs on windows, linux and macos.

sofar only openoffice provides this, but it is really slow.

any recommendations, one thing to consider is that installation should be as painless as possible...in fact i dont want to be there when they do install it.

---

### Post by LaRoza on 2008-01-02
> **airtonix said:**
> OK so im trying to find a dbase frontend like access that runs on windows, linux and macos.

sofar only openoffice provides this, but it is really slow.

any recommendations, one thing to consider is that installation should be as painless as possible...in fact i dont want to be there when they do install it.

Well, this thread is on SQLite and it is in a programming forum, so I will recommend using SQLite and writing your own front end. If that doesn't answer the question, then this is the wrong thread to ask in.

---

### Post by UbuWu on 2008-01-02
> **kaervas59 said:**
> I'm looking for a SQLite database administration tool (GUI).

Do you have some recommendation?

yes, [Sqliteman]("http://sqliteman.com/")

---

### Post by ccpizz on 2009-02-26
There are tons of GUIs listed at the official SQLite site:

 [http://www.sqlite.org/cvstrac/wiki?p=ManagementTools](http://www.sqlite.org/cvstrac/wiki?p=ManagementTools)

---

### Post by DocForbin on 2009-02-26
The firefox one works great I used to use it all the time.

---

### Post by stevescripts on 2009-02-27
From the quick and simple point of view, check out the dbedit.tcl and sqlitecon.tcl scripts on the SQLite website.

One might find these especially useful, as a place to start hacking out their own front end ...

Steve
(if you cant find them, ping me)

---

### Post by Bln on 2011-01-03
Well then, [SQLite Manager for Firefox]("http://code.google.com/p/sqlite-manager/") works very fine, while others (sqliteman, sqlitebrowser, knoda, etc.) are buggy (Qt bug, as example), corrupt sqlite files, and don't have a lot of options.

If you use vimperator, however, the way to start it is ```
:emenu Tools.SQLite Manager
```

And, in the end, if you plan to use SQLite Manager often, I'd highly recommend you to use the xul version (with xulrunner).

---

