---
title: "Newbie C++ question"
date: 2008-02-29
forum: Programming Talk
---

### Post by MysticOdin on 2008-02-29
How do I:
[LIST=1]
[*]Create a text file?
[*]Change a file/folder name?
[*]run/execute a file?
[/LIST]
from inside my program, I wish u can supply me with sample codes, thx.

---

### Post by Mickeysofine1972 on 2008-02-29
> **MysticOdin said:**
> How do I:
[LIST=1]
[*]Create a text file?
[*]Change a file/folder name?
[*]run/execute a file?
[/LIST]
from inside my program, I wish u can supply me with sample codes, thx.

you can take a look at the library ifstream which you can include by typing:
```
#include <ifstream>
```
this will let you read/write files 

Mike

---

### Post by MysticOdin on 2008-02-29
that helped in creating a text file, writing in it, & reading from it, now for the other two question any1?

---

### Post by PaulFr on 2008-02-29
I would suggest you look up **rename** and **system** functions using man pages or your IDE help.

---

### Post by MysticOdin on 2008-02-29
to run/execute a file I have include <stdlib.h> and use the system() function, e.g.: to run calculator```
 system("calc")
```; that leaves one question, how to rename a file/folder?

---

### Post by eye208 on 2008-02-29
To install the manual pages for Linux system calls, enter

sudo apt-get install manpages-dev

Then enter

man 2 rename
man 2 execve
man 2 fork

rename() renames or moves a file (within the same physical volume).

execve() loads and executes a program. This call will _not_ return because the new program completely replaces the old one within the running process. If you want the old program to continue running, you must use fork() to create a child process first which then calls execve().

---

### Post by Kazade on 2008-02-29
I would also consider boost::filesystem it is a bit daunting but once you get going with it it's a far better way of manipulating files like this:

```
#include <boost/filesystem.hpp>

namespace fs = boost::filesystem

fs::rename( "somedir", "somedir2" );
```

There is an example here: [http://beans.seartipy.com/2006/05/28/c-boost-filesystem-librarypart-ii-example-programs/](http://beans.seartipy.com/2006/05/28/c-boost-filesystem-librarypart-ii-example-programs/)

You can install it on ubuntu with:

sudo apt-get install libboost-filesystem-dev

---

