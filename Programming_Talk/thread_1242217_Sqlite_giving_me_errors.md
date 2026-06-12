---
title: "Sqlite giving me errors"
date: 2009-08-16
forum: Programming Talk
---

### Post by Gannon8 on 2009-08-16
I installed libsqlite3. Made a program. Worked for awhile, but now its not working. Whenever I use sqlite3_prepare_v2, it returns the error code 21 (SQLITE_ERROR_MISUSE, saying I did something wrong in my program). I have no idea what I did wrong though. Source attached, rename it to sqlite.c . MM_sqlite is a function called when the library is loaded. Don't worry about anything not too obvious.

BTW asss stands for A Small Subspace Server.

---

### Post by Arndt on 2009-08-17
> **Gannon8 said:**
> I installed libsqlite3. Made a program. Worked for awhile, but now its not working. Whenever I use sqlite3_prepare_v2, it returns the error code 21 (SQLITE_ERROR_MISUSE, saying I did something wrong in my program). I have no idea what I did wrong though. Source attached, rename it to sqlite.c . MM_sqlite is a function called when the library is loaded. Don't worry about anything not too obvious.

BTW asss stands for A Small Subspace Server.

You could reduce the program a little before asking others to debug it. But more importantly, where are asss.h and reldb.h?

---

### Post by Gannon8 on 2009-08-17
asss.h contains various server functions, accessed through the structures Iconfig (*.conf parser) and Ilogman (logger). It also defines some structures, but the only one in use is MPQueue. It also has "#define local static", amalloc (error handling and sets memory to 0), and afree(pretty much no difference).

Reldb is the header file for this file. There aren't any structure declarations besides the interface itself, which doesn't get used until the very bottom.

Yeah, I wanted to shorten it, but I couldn't really think of anyway to do it without missing anything important. Sorry :(

---

