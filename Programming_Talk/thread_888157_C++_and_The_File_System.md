---
title: "C++ and The File System"
date: 2008-08-12
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-08-12
I need a good guide/reference/tutorial on using C++ to deal with the file system, If one exists?!?

I need to know how to 
[LIST]
[*]read file names from a directory (ls)
[*]create a new file without accidentally deleting an existing files contents (touch)
[*]create a folder (mkdir)
[/LIST]

---

### Post by hod139 on 2008-08-12
Boost filesystem is one option: [http://www.boost.org/doc/libs/1_35_0/libs/filesystem/doc/index.htm](http://www.boost.org/doc/libs/1_35_0/libs/filesystem/doc/index.htm)

---

### Post by Mr.Macdonald on 2008-08-13
I would prefer to not install boost

---

### Post by tuxerman on 2008-08-13
The system() function can also be used for stray purposes.

system("mkdir newdir"); //for example

You'll have to include the stdlib header file.

---

### Post by Jessehk on 2008-08-13
If you're on Ubuntu, an unportable way of doing it would be using the POSIX functions that come with glibc.
You can see the documentation for them [here](http://www.gnu.org/software/libc/manual/html_node/File-System-Interface.html#File-System-Interface).

The Boost libraries are portable and would probably be a better choice.

---

### Post by nrs on 2008-08-13
Looking around you get the impression people see Boost as a Meg.

---

### Post by LaRoza on 2008-08-13
> **Mr.Macdonald said:**
> I need a good guide/reference/tutorial on using C++ to deal with the file system, If one exists?!?

I need to know how to 
[LIST]
[*]read file names from a directory (ls)
[*]create a new file without accidentally deleting an existing files contents (touch)
[*]create a folder (mkdir)
[/LIST]

C has functions for those tasks, so C++ will have access to them. stdio.h and stdlib.h would have them, so start in the C++ versions of those.

For the second option, you'd have to test if a file exists then create it, not hard.

---

### Post by dwhitney67 on 2008-08-13
> **Mr.Macdonald said:**
> I would prefer to not install boost
Boost is your best choice if you prefer portability of your code.  If you are more interested in the nuts-n-bolts of how things are done, then research the following C-library functions:
[LIST]
[*]opendir()
[*]readdir()
[*]mkdir()
[*]unlink()
[*]stat()
[/LIST]
For creating a file, use std ofstream, or fall back on the C-library's open() or fopen().

Avoid using the system() command unless you have a clear understanding of its limitations.

---

### Post by Mr.Macdonald on 2008-08-13
I fixed the second thing i wanted, i just had a bug in my code!!

I will probably use boost, but is boost statically linked or dynamically?

If it is dynamically then that means that my user would need boost installed right?

I would prefer static, i think

scratch that i just learned that boost is header only, I love it!!

---

### Post by Zugzwang on 2008-08-14
> **Mr.Macdonald said:**
> I will probably use boost, but is boost statically linked or dynamically?

If it is dynamically then that means that my user would need boost installed right?

[...]

scratch that i just learned that boost is header only, I love it!!

Not precisely true. There are parts that need to be linked. However, you *can* link it statically, if you want to.

---

