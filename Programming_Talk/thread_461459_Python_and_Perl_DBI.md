---
title: "Python and Perl DBI"
date: 2007-06-01
forum: Programming Talk
---

### Post by jordilin on 2007-06-01
Is there sth like Perl DBI in Python. Perl DBI supports a large quantity of databases, such as mysql, postgres, informix, ... and your code does not vary. In Python you need different modules depending on the database you use, informixdb for informix pg for postgres. Is there just a module for all the dbs in python? I like Python, and I am totally frustrated about using Perl DBI. Another question. For general, sys admin scripting what's better, python or perl?

---

### Post by pmasiar on 2007-06-01
Yup, ODBC drivers would be nice to have... :-(

Python is more readable, especially in bigger programs.
For little programs, oldtimers still prefer Perl, also because it has more functionality in core languages (like regular expresions) -- which is a bug from POV of Python :-)

---

### Post by ghostdog74 on 2007-06-01
> **jordilin said:**
> Is there sth like Perl DBI in Python. Perl DBI supports a large quantity of databases, such as mysql, postgres, informix, ... and your code does not vary.

sure, there is [mxODBC]("http://www.egenix.com/files/python/mxODBC.html") for example. Also check out [pyPerl]("http://wiki.python.org/moin/PyPerl"). It has a module that wraps around Perl's DBI even. However you can also use one that is particular to your database, see [here]("http://www.python.org/topics/database/modules.html"). These database modules are written to conform to DB specs, so a connect() in one db module should be the same in another. minimal changes to your script if you were to switch databases.

>  Another question. For general, sys admin scripting what's better, python or perl?
There's no such things as a better language. It all depends on you, what's your needs/tasks you are doing and also environmental conditions.(if you can't install Python, for eg) I am  a sysadmin by job nature and have used Perl for sysadmin scripting way before Python. Occasionally i still write simple one liners in Perl to do simple task..but have since switched to Python if i need to write long scripts, for readability and maintenance's sake. Of course, that's just me.

---

### Post by hasimir44 on 2007-06-01
perl is (generally) already installed when it comes to *nix, and if you work somewhere like my work, then you can't just go installing anything you want on the servers because you feel like it. that said - i like perl and use it quite a bit. i hear all the time how "perl is ugly", but it doesn't have to be. if you want to write short and ugly code you can, but you can also write very readable code in perl..

i have to say though - i've started reading the pickaxe book and ruby seems to have everything that's cool about perl and then some.. i think i'm the only one at my work learning ruby though, so there's no way that it's getting installed there any time soon..

---

