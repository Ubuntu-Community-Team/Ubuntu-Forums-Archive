---
title: "Undefined reference to yyparse (flex &amp; bison)"
date: 2010-07-20
forum: Programming Talk
---

### Post by ukblacknight on 2010-07-20
I'm trying to run an example that's in the book "Flex & Bison".  I've written out my own examples, and also downloaded the examples available from the o'reily FTP site, both of which won't run.

The relevant files are (remove the .txt extension):
fb3-1.l
fb3-1.y
fb3-1.h
fb3-1funcs.c

To build, you run:
```

bison -d fb3-1.y
flex -ofb3-1.lex.c fb3-1.l
cc -o $@ fb3-1.tab.c fb3-1.lex.c fb3-1funcs.c

```

Which is giving me the following error:
```

/tmp/ccNoe5BR.o: In function `yylex':
fb3-1.lex.c:(.text+0x2d5): undefined reference to `yylval'
/tmp/ccPI4ubH.o: In function `main':
fb3-1funcs.c:(.text+0x420): undefined reference to `yyparse'
collect2: ld returned 1 exit status

```

I've got flex-old and bison installed, so I can't figure this one out :\  I've also tried using the 'flex' package rather than 'flex-old', but that doesn't seem to make a difference.

Anyone got any ideas?

---

### Post by gmargo on 2010-07-20
Using standard flex (not flex-old) it compiles and links for me, on 10.04 Lucid.

BTW, PLEASE don't use pastebin - it takes time to download and rename those files. This forum supports attachments; you could have just attached them.

---

### Post by ukblacknight on 2010-07-21
I've just tried it with 'flex' and it made no difference.  I also installed Ubuntu 9.10 in a VM and tried it on there, same error :\

Did you definitely do:

```

flex -ofb3-1.lex.c fb3-1.l

```

and not:

```

flex -o fb3-1.lex.c fb3-1.l

```

---

### Post by gmargo on 2010-07-21
On the flex command line, I originally used a space between the -o and the filename.  Going back and redoing it, with or without the space, I get exactly the same generated fb3-1.lex.c file.

BTW, your link line is suitable for a makefile but not the command line.  I replaced the "$@" with a valid file name.  This is your problem - the "$@" expands to nothing, so gcc trys to write the output file on fb3-1.tab.c instead of compiling it - I can duplicate your error now.

```

$ ls -lGg
total 16
-rw-r--r-- 1  562 Jul 21 09:35 fb3-1.h
-rw-r--r-- 1  457 Jul 21 09:35 fb3-1.l
-rw-r--r-- 1  788 Jul 21 09:35 fb3-1.y
-rw-r--r-- 1 1772 Jul 21 09:35 fb3-1funcs.c

$ bison -d fb3-1.y

$ flex -ofb3-1.lex.c fb3-1.l

$ cc -o fb3 fb3-1.tab.c fb3-1.lex.c fb3-1funcs.c

$ ls -lGg
total 136
-rwxr-xr-x 1 22510 Jul 21 09:37 fb3
-rw-r--r-- 1   562 Jul 21 09:35 fb3-1.h
-rw-r--r-- 1   457 Jul 21 09:35 fb3-1.l
-rw-r--r-- 1 47140 Jul 21 09:37 fb3-1.lex.c
-rw-r--r-- 1 42781 Jul 21 09:37 fb3-1.tab.c
-rw-r--r-- 1  2190 Jul 21 09:37 fb3-1.tab.h
-rw-r--r-- 1   788 Jul 21 09:35 fb3-1.y
-rw-r--r-- 1  1772 Jul 21 09:35 fb3-1funcs.c

$ flex --version
flex 2.5.35

$ bison --version
bison (GNU Bison) 2.4.1
(snip)

gmargo@euler 2147$ cc --version
cc (Ubuntu 4.4.3-4ubuntu5) 4.4.3
(snip)

```

---

### Post by ukblacknight on 2010-07-21
Excellent! Thanks very much!  Not really sure why the book didn't make that explicit for n00bs like myself :)

---

