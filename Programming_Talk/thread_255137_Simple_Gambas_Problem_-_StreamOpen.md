---
title: "Simple Gambas Problem - Stream/Open"
date: 2006-09-11
forum: Programming Talk
---

### Post by az_human on 2006-09-11
So I'm fiddling around with Gambas (1.0.13) and trying to open a stream to a file using the stock example provided on the documentation wiki:

----------------------------------
  DIM hFile AS File
  DIM sLine AS String

  hFile = OPEN "/home/userhere/filehere.txt" FOR INPUT

  WHILE NOT Eof(hFile)
    LINE INPUT #hFile, sLine
    PRINT sLine
  WEND
----------------------------------
The above would respond to a simple event such as a button click.  However, when I try and run the app, it immediately gives me:

Syntax error at line 11 in Form1.class

The line number refers to the "hFile = OPEN...." line.

As I said, I'm extremely new to Gambas, but it looks fun.  Trying to get the hang of the simple stuff.

Thanks in advance for anybody who can provide any input to the syntax error.

---

### Post by DoktorSeven on 2006-09-11
Syntax is:

```
OPEN File name FOR [ READ ] [ WRITE ] [ CREATE | APPEND ] [ DIRECT ] [ WATCH ] [ BIG | LITTLE ] AS # Variable 
```

So maybe you're looking for:
```
 OPEN "/home/user/file.txt" FOR READ AS #hFile
```

---

### Post by az_human on 2006-09-11
Thanks!  I appreciate it.

However, it's frustrating that the Gambas documentation here [http://gambasdoc.org/help/lang/open?en](http://gambasdoc.org/help/lang/open?en) shows a little differently.  I did look in the local help file and it shows it as you do, so maybe I'll follow the local help material instead of the wiki.

Thanks again.

---

### Post by fontenot_1031 on 2006-09-14
I just downloaded the newest Gambas stable, but the readme howto install text document from a user of Debian was hard to understand (missing words, etc).  Will the Debian readme work?  Or does anyone have the Ubuntu readme?

---

