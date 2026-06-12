---
title: "sqlite and python"
date: 2009-12-12
forum: Programming Talk
---

### Post by DanielJackins on 2009-12-12
Does anyone know of any good sql/sqlite tutorials on the web? All I can seem to find seems to assume previous knowledge of SQL, and it's a bit confusing. Specifically I hope to use sqlite along with python, so if there's anything pertaining to that that would be great.

Also - if I wanted to make, say, a simple text game with python where your progress could be saved, how would I go about doing that? Using databases? Or simply creating text files which the program reads from?

Thanks for any help

---

### Post by -grubby on 2009-12-12
SQLite isn't terribly hard to understand. [http://www.w3schools.com/SQl/sql_intro.asp](http://www.w3schools.com/SQl/sql_intro.asp) is a good introduction to SQL in general. After you've learned SQL, see [http://souptonuts.sourceforge.net/readme_sqlite_tutorial.html](http://souptonuts.sourceforge.net/readme_sqlite_tutorial.html) for a tutorial with specific SQLite syntax and then [http://docs.python.org/library/sqlite3.html](http://docs.python.org/library/sqlite3.html) for documentation on using SQLite in Python.

As for saved games -- both methods would work fine, though if you used an SQLite database you wouldn't have to deserialize/serialize any text files.

---

### Post by era86 on 2009-12-12
> **DanielJackins said:**
> Does anyone know of any good sql/sqlite tutorials on the web? All I can seem to find seems to assume previous knowledge of SQL, and it's a bit confusing. Specifically I hope to use sqlite along with python, so if there's anything pertaining to that that would be great.

Also - if I wanted to make, say, a simple text game with python where your progress could be saved, how would I go about doing that? Using databases? Or simply creating text files which the program reads from?

Thanks for any help

If it is just a simple text game, I wouldn't use a database to store the information.  You could simply store it as binary data because I imagine the information you need isn't too complex.  I don't think saving the state of a text game warrants a database.

---

