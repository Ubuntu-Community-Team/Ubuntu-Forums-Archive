---
title: "gdb issue"
date: 2009-01-03
forum: Programming Talk
---

### Post by Cyclops_ on 2009-01-03
Hey, all,

I am trying to get "clewn" to work so that I can do PHP debugging with gVim through gdb.

I have clewn installed and gdb and vim (even upgraded to vim 7.2) ...

I will run clewn, which brings up an instance of gvim and starts gdb. Then when I try to set a breakpoint, I run into the following error (in gdb):

 	```
 	No symbol table is loaded.  Use the "file" command. 

```
I tried compiling gdb from source, and attempted to "compile with the -g option" (or tried to figure out how to do that anyway).... since I am a complete n00b at compiling things beyond the basic ./configure, make, make install.....

Any help would be GREAT!

Thanks!!!

---

### Post by dexter on 2009-01-04
I'm not familiar with clewn, but is gdb associated with the executable you are trying to run? You can associate it with the file command from gdb:
```
file path_to_executable
```
Or you can start gdb with you executable as an argument
```
gdb path_to_executable
```

---

### Post by Cyclops_ on 2009-01-04
Yes.  I just tried it with _only_ gdb (no clewn, no vim)...  so I'm pretty sure it's a gdb issue.  I started up gdb with the gdb command, and then typed "file xxxx.php" .... and then when I typed "break 57" it gave me that error.

---

### Post by monkeyking on 2009-01-04
Can you clarify if you can run your program with gdb from the promt like


```
g++ -g yourcode.cpp
gdb ./a.out 
```

Or aren't you trying debug a c/c++ file?

---

### Post by Cyclops_ on 2009-01-04
Well, I think I am one step closer to figuring things out (or helping someone else help me figure them out.)  After the last question, I tried a few things, and noticed a few things:

First, I am not using gdb to debug an executable.  I am trying to get it to debug PHP.

Here is what I get when I try a couple of things:

```

user@compy:/var/www/my_site/private/app/controllers$ gdb
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
(gdb) file admins_controller.php
"/var/www/my_site/private/app/controllers/admins_controller.php": not in executable format: File format not recognized
(gdb) break "/var/www/movimasala/cake_private/app/controllers/admins_controller.php:70"
No symbol table is loaded.  Use the "file" command.
(gdb)

```

Does this help anyone?

---

### Post by monkeyking on 2009-01-04
I've never used gdb to debug php, I didn't even know it could do it, are you sure it can.

Maybe you should try with dbg [http://www.php-debugger.com/dbg/](http://www.php-debugger.com/dbg/)

---

