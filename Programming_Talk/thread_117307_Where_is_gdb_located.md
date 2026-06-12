---
title: "Where is gdb located?"
date: 2006-01-14
forum: Programming Talk
---

### Post by YourSurrogateGod on 2006-01-14
I need to do some stuff in regards to C++ STL and I don't know where it is.

---

### Post by Zelut on 2006-01-14
have you tried: **locate <package/file/etc>** ?

...you may need to **sudo updatedb** to update the index, but that is very useful in finding programs, files, etc.

---

### Post by YourSurrogateGod on 2006-01-14
Actually, I've never known that there is such a function.

---

### Post by Zelut on 2006-01-14
:)  there are lots of those little functions that I'm sure it'll still late years to master.  **locate **& **whereis **work similarly, I prefer locate.  I hope that works for you..

---

### Post by YourSurrogateGod on 2006-01-14
Odd... I expected .gdbinit to be where gdb is, but it's not... where's .gdbinit located :) ?

I tried locate and whereis and couldn't find either.

---

### Post by toojays on 2006-01-14
If you want a gdbinit file, you need to create it yourself; it lives in your home directory. See section 2.1.3 of the gdb manual for details.

---

### Post by YourSurrogateGod on 2006-01-19
I've went to [here](http://sources.redhat.com/gdb/onlinedocs/gdb_3.html#SEC10), but I still don't understand how I should set up .gdbinit. I then tried to simply create one with gedit and then insert this line into it (in my home directory.)
```
source ~/.gdb/gdb_stl_utils
```
I got the below errors as a result of that...
```
GNU gdb 6.3-debian
Copyright 2004 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i386-linux"...add symbol table from file [b]"/home/andrew/.gdb/StlStdContainers.o" at
/home/andrew/.gdbinit:1: Error in sourced command file:
/home/andrew/.gdb/gdb_stl_utils:21: Error in sourced command file:
"/home/andrew/.gdb/StlStdContainers.o": can't read symbols: File format not recognized.[/b]
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
```

---

### Post by jerome bettis on 2006-01-19
have you thought of apt-getting DDD (gui frontend to gdb, looks old but very nice) and just using that

---

### Post by Viro on 2006-01-20
I vouch for DDD or Insight, both of which are good front ends to gdb.

---

### Post by YourSurrogateGod on 2006-01-20
[QUOTE=Viro]I vouch for DDD or Insight, both of which are good front ends to gdb.[/QUOTE]
I take it that you're able to see values inside of STL objects (i.e. string or list classes) just like in .NET with ease?

---

### Post by Viro on 2006-01-21
No, you won't be able to see inside STL classes with ease. I don't think you can do this even with MSVC, mainly because of the way the STL is coded (methods being inlined, etc). Have a go at it and see what I mean.

---

### Post by YourSurrogateGod on 2006-01-21
[QUOTE=Viro]No, you won't be able to see inside STL classes with ease. I don't think you can do this even with MSVC, mainly because of the way the STL is coded (methods being inlined, etc). Have a go at it and see what I mean.[/QUOTE]
I've yet to encounter any problems with debugging STL stuff in either Visual Studio 6.0 and .NET.

---

### Post by YourSurrogateGod on 2006-01-21
Just curious, but has anyone else tried to set up gdb (or some other debugger) so that it allows you to debug STL objects/classes? If so, how did you do it?

I'd like to hear a different take on this.

---

### Post by Viro on 2006-01-21
Hmm, perhaps MSVC comes with a different set of STL headers, release headers that are inlined, and debug headers that aren't?

Anyway, here are some utilities that may be of use to you. [http://staff.science.uva.nl/~gilad/stl/stl_gdb.html](http://staff.science.uva.nl/~gilad/stl/stl_gdb.html) and some updated stuff [here](http://www.stanford.edu/~afn/gdb_stl_utils/).

---

### Post by YourSurrogateGod on 2006-01-21
[QUOTE=Viro]Hmm, perhaps MSVC comes with a different set of STL headers, release headers that are inlined, and debug headers that aren't?[/quote]
I dunno, I'll ask one of my friends who's a big Windows buf.
[quote=Viro]Anyway, here are some utilities that may be of use to you. [http://staff.science.uva.nl/~gilad/stl/stl_gdb.html](http://staff.science.uva.nl/~gilad/stl/stl_gdb.html) and some updated stuff [here](http://www.stanford.edu/~afn/gdb_stl_utils/).[/QUOTE]
Yeh, I know about that last site. It tells me that I should put "source ~/.gdb/gdb_stl_utils" in my .gdbinit file. I looked in the gdb manual in order to figure out how to create that file, but I didn't get the answer that I needed. Which leaves me where I am right now...

---

