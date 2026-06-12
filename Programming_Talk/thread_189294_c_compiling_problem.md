---
title: "c compiling problem"
date: 2006-06-05
forum: Programming Talk
---

### Post by Eclipsor on 2006-06-05
Hi all. I'm trying to compile a program I'm doing for a uni assignment using a script given to us (see below). It worked in Breezy however in Dapper I am getting this error: 

/usr/bin/ld: cannot find -lXmu
collect2: ld returned 1 exit status

```
gcc $1.c -o $1 -I/usr/share/pvm3/include -L/usr/share/pvm3/lib/LINUX -L/usr/X11R6/lib -lpvm3 -lglut -lGL -l GLU -lXmu -lXi -lXext -lX11 -lm
```

I'm a bit of a linux noob so any help would be very much appreciated. Also, let me know if there is any more info I should provide. Thanks.

ps. I didn't do a straight upgrade so there might be some packages that I had installed on breezy that aren't there now but I've tried installing anything that looked like it might be needed.

---

### Post by Eclipsor on 2006-06-05
update

Seems it works so far without that -lXmu section in the compile line. Can anyone tell me what this would do? thanks

---

### Post by Arndt on 2006-06-05
[QUOTE=Eclipsor]update

Seems it works so far without that -lXmu section in the compile line. Can anyone tell me what this would do? thanks[/QUOTE]

The entry libxmu6 in Synaptic says "X miscellaneous utilities". It doesn't seem to include man pages, only a header file, but there are some functions in it called XmuNewArea etc. If you get an undefined symbol while linking, named something starting with Xmu, you know you'll need to get this package.

---

### Post by Eclipsor on 2006-06-06
I had the libxmu6 package installed but I installed a few of the other dev packages and stuff and it works now. Thanks.

---

