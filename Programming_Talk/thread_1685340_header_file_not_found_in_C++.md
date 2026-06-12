---
title: "header file not found in C++"
date: 2011-02-10
forum: Programming Talk
---

### Post by debd on 2011-02-10
I have to run a program using these headerfiles 
general.h
poll.h
and
snmppoll.h

what package should I install for having this headerfiles in place?

..also I want to know where are all the headerfiles saved in linux. I have quite a big header file library in windows. It would be usefull if I can copy those files to the linux directory where .h files are kept.

btw, I'm using the Geany IDE.

---

### Post by MadCow108 on 2011-02-10
header files from packages are installed in /usr/include
user installed files should go in /usr/local/include (which is not searched by the compiler by default) to not be overwritten by package contents

you can use apt-file to search for packages containing your needed files. but the names are so general I doubt that will be very helpful.

---

### Post by debd on 2011-02-10
> but the names are so general I doubt that will be very helpful.
 but geany keeps on saying the headers aren't found.
 will the compiler search for the files in /usr/local/include if not found in /usr/include?

---

### Post by debd on 2011-02-10
ok ..I found general and poll .
though Geany refuses to have found it.
snmppoll is missing. :|

---

### Post by MadCow108 on 2011-02-10
> **debd said:**
> but geany keeps on saying the headers aren't found.
 will the compiler search for the files in /usr/local/include if not found in /usr/include?

no you have to tell it where to look with the -I flag.
[PHP]gcc file.c -I/usr/local/include[/PHP]
in geany this can be set under build -> set build options

there are 45 packages in the archive which provide a poll.h
without context on what you need you'll not find the correct one.

---

### Post by debd on 2011-02-10
the general is in .hpp
is it similar with .h?
ain't working..

help me setting the dir to find the necessary headers?
pls see the attachment.

thanks for your efforts. :)

---

### Post by MadCow108 on 2011-02-10
are you compiling a single file or multiple files?
do you have makefile?
what is your projects directory layout?
please show your code
...
please show the exact error message and all information needed to reproduce the problem, else its just guessing.

---

### Post by Arndt on 2011-02-10
> **debd said:**
> I have to run a program using these headerfiles 
general.h
poll.h
and
snmppoll.h

what package should I install for having this headerfiles in place?



If you don't try to include them (comment out the include directives), some useful error message will probably appear about something missing. Then you may have something more specific to give to Google.

---

### Post by Zugzwang on 2011-02-11
@OP: Actually, there is no Ubuntu package containing a file named "snmppoll.h". Is it possible that your header files are part of the project you are trying to compile?

---

### Post by debd on 2011-02-11
> @OP: Actually, there is no Ubuntu package containing a file named "snmppoll.h". Is it possible that your header files are part of the project you are trying to compile?

...I actually never thought about that
after a bit of googling I'm sure bout it now.
thanks for pointing out.
we actually have been given a source file to manipulate some aspects of the design...college staff :)

---

