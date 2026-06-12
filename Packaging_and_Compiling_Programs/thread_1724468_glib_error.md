---
title: "glib error"
date: 2011-04-08
forum: Packaging and Compiling Programs
---

### Post by debd on 2011-04-08
yesterday I unknowingly(I mean I didnt understand it was not really needed :/)  compiled and installed glib2.27.92  while glib-2.26.1 was present and that made a big mess of my system.

```
dpkg -r glib-2.27.92
``` 
didn't work saying 

**dpkg: warning: ignoring request to remove glib-2.27.92 which isn't installed.**

 Lastly, I removed some of the glib.so files of the later version(2.27.92) and it is back to normal i.e. I have no problem for normal using. however, there are obvious traces of it throughout my system and pkg-config info files. I cant compile any source requiring glib coz glib-config can't be found. rather its confused with pkg-config telling that latest ver. of glib is 2.27.92 though 2.26.0 is also found  :(


I checked:

```
pkg-config --libs "glib >= 2.6"
```

```
pkg-config --exists glib
```

both gives :

```
sh: glib-config: not found
sh: glib-config: not found
sh: glib-config: not found
```

is there a way around to get over this?

thanks in advance for any help and suggestions.

---

### Post by MadCow108 on 2011-04-08
the glib2 .pc file is glib-2.0
```

pkg-config --exists glib-2.0
```

pkg-config --exists glib gives the same error on my system too. Its probably some relict from glib1

did you install 2.27 via a package or configure, make, make install?
the latter installs into /usr/local by default and should thus not interfere with the 2.26 package

to make sure the installation is alright install debsums and run it on all glib2 packages:
```
debsums libglib2.0-dev
```

---

### Post by debd on 2011-04-08
> did you install 2.27 via a package or configure, make, make install?
the latter installs into /usr/local by default and should thus not interfere with the 2.26 package

I compiled and installed.
I believe the glib.pc files of the later ver. I deleted manually were in /usr/local.

the glib-2.0.pc files are currently in  /usr/local/lib/pkgconfig .

though now,

```
pkg-config --exists glib-2.0 | echo $?
```

gives '0'.

reinstalling glib-2.0 from synaptic didn't help.

and I dont know about the debsum package you mentioned. the name looks like it detects package integrity ?

anyway, I'll give it a try.

thanks.

---

### Post by debd on 2011-04-08
debsum helped   :popcorn:

I found the .pc files of the later ver. of glib in /usr/local/lib

deleted them all; and reinstalled libglib2.0-dev .
and now 
```
pkg-config --modversion glib-2.0
```

gives 2.26.1 :D 

though 
```
pkg-config --exists glib-2.0 | echo $?
```

gives that same infamous big '0'

thanks.

---

### Post by MadCow108 on 2011-04-08
> **debd said:**
> 
though 
```
pkg-config --exists glib-2.0 | echo $?
```

gives that same infamous big '0'

thanks.

0 is good.
on unix systems (and most others too) 0 is the OK return code.
values different than 0 indicate errors.

but your command is still wrong.
the pipe | forks a new process and messes with the return code (I actually do not even know what $? evaluates to in this situation).
you usually do something like this:
```
pkg-config --exists glib-2.0 && echo "yes"
```
here the later is only executed when the former returns 0

---

