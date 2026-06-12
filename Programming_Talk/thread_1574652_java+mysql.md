---
title: "java+mysql"
date: 2010-09-14
forum: Programming Talk
---

### Post by navaneethan on 2010-09-14
I forward this thread to be solved here ,Unfortunately it was posted in misplace  click here [http://ubuntuforums.org/showthread.php?t=1574622](http://ubuntuforums.org/showthread.php?t=1574622)

---

### Post by r-senior on 2010-09-14
```

ResultSet result = stat.executeQuery("INSERT INTO STUDENT VALUES(string[0],string[1],string[2],string[3],string[4],string[5],string[6],string[7],string[8]");

```

I think your problem is that you are mixing Java code into a string that will be passed direct to the database, i.e. "INSERT INTO STUDENT VALUES(string[0]...)".

You need to either do something ugly like this:

```

stat.executeQuery("INSERT INTO STUDENT VALUES('" + string[0] + "', '" + ...)

```

or, preferably, use a [prepared statement](http://download.oracle.com/javase/tutorial/jdbc/basics/prepared.html), which is both more efficient and easier to maintain.

---

