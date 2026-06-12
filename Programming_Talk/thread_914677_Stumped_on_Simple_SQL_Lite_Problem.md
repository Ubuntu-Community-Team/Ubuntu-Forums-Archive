---
title: "Stumped on Simple SQL Lite Problem"
date: 2008-09-09
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-09-09
I compile this code:

```

#include "SQLiteRec.h"
#include <stdio.h>
#include <stdlib.h>
#include <string>

using namespace std;

int main()
{
	SQLiteDB db("somedb.db3");
	
	char* query = "SELECT cat, mouse, field2 from animals ORDER BY ROWID;";

	if (!db.isConnected())
	 {
		 printf("Database not connected.");
	 }
	 
	db.Open(query);

	return 0;
}

```

And then run it on the SQL Lite database, somedb.db3, which was created using the following commands: 

```

BEGIN TRANSACTION;
CREATE TABLE animals (field2 TEXT, mouse TEXT, cat TEXT);
INSERT INTO animals VALUES('df','hello','good');
INSERT INTO animals VALUES(NULL,'','bad');
INSERT INTO animals VALUES('asf','star','garbage');
COMMIT;

```

When I execute the program above, it crashes.  I don't see why.  Anyone see the problem?  I have been stumped on this for the past 4 hours.

---

### Post by SNYP40A1 on 2008-09-09
Actually, I think it is the NULL value that is causing problems.  I noticed that after posting and changed it to '', and now my program runs without crashing -- at least up to the open command.  So if a column is labeled as TEXT, every column must contain a string, including possibly the empty string.  In other words, NULL or any other non-quoted values are not legitimate?

---

### Post by stevescripts on 2008-09-09
SNYP40A1 ... a question...

Are you using some sort of C++ lib with sqlite?  (I do not recognize the header  #include "SQLiteRec.h" ...)

There is nothing wrong with your SQL - I created an sqlite db from your example and ran your query from a little c program:

(the program name is what, and the db I created is called try.db)

```

steveo@delldesktop:~/Desktop$ ./what try.db "SELECT cat, mouse, field2 from animals ORDER BY ROWID;"
cat = good
mouse = hello
field2 = df

cat = bad
mouse = 
field2 = NULL

cat = garbage
mouse = star
field2 = asf

```

You may find [http://www.sqlite.org/quickstart.html](http://www.sqlite.org/quickstart.html) helpful, I know that I do ;)

---

