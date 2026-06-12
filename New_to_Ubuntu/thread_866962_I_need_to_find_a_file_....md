---
title: "I need to find a file ..."
date: 2008-07-22
forum: New to Ubuntu
---

### Post by larry19l on 2008-07-22
Hi Folks,
I need to be able to find a file ...
Whereis --help is particularly uninformative: 1 line !
What I'm looking for is a means of locating any file with wildcards such that the output of the program looks like this in a terminal window:

~$whereisthatfile / *.?r?
completepathfromroot/filename.filetype
completepathfromroot/nextfilename.filetype
.
.
.

---
Anyone ?

Cuz, lotsa times, here and as a result of a program failure, I get sent on some wild goose hunt for some config file that either doesn't exist(yet) or has the wrong stuff in it, but I'm supposed to edit it. How am I supposed to edit it if I don't know where it is !? Like, gedit filname.typ in a code box is a particularly nasty way to waste someone's time.

---

### Post by northern lights on 2008-07-22
Use the "locate" command...

```
~$locate Filename
```
or
```
~$locate StartOfFilename*
```

---

### Post by scorp123 on 2008-07-22
> **larry19l said:**
> Hi Folks,
I need to be able to find a file ... ```
find /where/to/look -name Name.Of.File -print
```

Examples:

```
> find /etc -name xorg.conf -print
/etc/X11/xorg.conf 
```

This works with relative paths too ... e.g. "." (dot) means "right here" (= your current location); so any result is relative to that (e.g. inside a sub-directory of your current location):

```
> find . -name '*.jpg' -print
./tmp/2008.07.22.18.07.16.jpg
./tmp/2008.07.22.18.01.39.jpg
./tmp/2008.07.22.18.04.59.jpg
./tmp/2008.07.22.18.02.12.jpg
./tmp/2008.07.22.18.04.11.jpg
./tmp/2008.07.22.18.08.06.jpg
./tmp/2008.07.22.18.04.49.jpg
./tmp/2008.07.22.18.08.14.jpg
./tmp/2008.07.22.18.05.02.jpg
./tmp/2008.07.22.18.08.18.jpg
./tmp/2008.07.22.18.05.06.jpg
./tmp/2008.07.22.18.04.21.jpg
./tmp/2008.07.22.18.02.05.jpg
./tmp/2008.07.22.18.06.20.jpg
./tmp/2008.07.22.18.08.10.jpg
./tmp/2008.07.22.18.03.22.jpg
./tmp/2008.07.22.18.04.54.jpg
./tmp/2008.07.22.18.02.49.jpg 
```

Another example: as superuser "root" find all files underneath /home with either the *.tmp, *.Tmp or *.TMP extension, print their name, and then have each of them automagically moved into a folder called "~/Temporary_Stuff" ...

```
> sudo find /home -name '*.[tT][mM][pP]' -print -exec mv {} ~/Temporary_Stuff/ \; 
```
...


Regards.

---

