---
title: "listing contents of a directory in C++ under Linux"
date: 2006-09-17
forum: Programming Talk
---

### Post by phorque on 2006-09-17
Hi, I'm really struggling to find any answer to my topic's dilemma. This is for a university project being done in C++.

All I'm wanting to do is get strings for all the files in a explicitly defined directory that end in ".profile"

The only thing I can think of doing would be to parse a...

```
system ("ls ./profiles/*.profiles");
```

... and I can't help but think that this is me being a n00b. Can somebody please tell me what library/classes/methods I should be importing and using to do this?

---

### Post by thumper on 2006-09-17
Not sure about what your uni allows, but how I'd do it is with [boost::filesystem](http://www.boost.org/libs/filesystem/doc/index.htm)

---

### Post by Lster on 2006-09-17
You could try using the C file system interface. See [http://www.gnu.org/software/libc/manual/html_node/Simple-Directory-Lister.html#Simple-Directory-Lister](http://www.gnu.org/software/libc/manual/html_node/Simple-Directory-Lister.html#Simple-Directory-Lister).

---

### Post by phorque on 2006-09-17
Ah, that's what I needed. Thanks so much for the tip! ;)

---

### Post by amo-ej1 on 2006-09-18
To be more exact: [http://www.gnu.org/software/libc/manual/html_node/Scanning-Directory-Content.html#Scanning-Directory-Content](http://www.gnu.org/software/libc/manual/html_node/Scanning-Directory-Content.html#Scanning-Directory-Content) describes the scandir() function see also *man 3 scandir*

```

       The scandir() function scans the directory  dir,  calling  filter()  on
       each  directory entry.  Entries for which filter() returns non-zero are
       stored in strings allocated via malloc(), sorted using qsort() with the
       comparison  function compar(), and collected in array namelist which is
       allocated via malloc().  If filter is NULL, all entries are selected.

```

Which should help you more in locating all *.profiles altough readdir and friends will work fine also.

---

