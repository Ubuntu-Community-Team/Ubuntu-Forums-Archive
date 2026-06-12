---
title: "Migration from MS Office to LibreOffice"
date: 2013-08-12
forum: New to Ubuntu
---

### Post by leonardo-ballabeni on 2013-08-12
Hi, i need to LINK a CSV file to a BASE.
For a professional use i need to download my csv file, put it in the same directory (everytime) and read it with a database.
I usually do it with MSO but with Base i could only IMPORT (passing through calc) not LINK.

Sorry for bad english (i'm Italian and in my forum nobody can help me).

Thanks

---

### Post by Zill on 2013-08-12
leonardo-ballabeni:  You might get useful help on [LibreOfficeForum.org]("http://it.libreofficeforum.org/")

---

### Post by oldfred on 2013-08-12
Welcome to the forums.

I used to download massive files from mainframe (really AS/400) and add them either to a SQL server or an Access data base. It was our full part number, BOM, router files for our factory. I would review, correct and script screen tasks to upload the corrections.

After retiring and converting to Ubuntu I looked for something similar. Not much but you end up rolling your own. I download stock prices as csv, use python to import into SQLite files and use those. If using a database it would be better to import than directly use csv files.

[http://docs.python.org/library/sqlite3.html](http://docs.python.org/library/sqlite3.html)

[http://zetcode.com/db/sqlitepythontutorial/](http://zetcode.com/db/sqlitepythontutorial/)

[http://www.halfcooked.com/presentations/osdc2006/python_databases.html](http://www.halfcooked.com/presentations/osdc2006/python_databases.html)

[http://en.wikipedia.org/wiki/Database_normalization](http://en.wikipedia.org/wiki/Database_normalization)

[http://en.wikipedia.org/wiki/Codd%27s_12_rules](http://en.wikipedia.org/wiki/Codd%27s_12_rules)

[http://stackoverflow.com/questions/41233/java-and-sqlite](http://stackoverflow.com/questions/41233/java-and-sqlite)

---

