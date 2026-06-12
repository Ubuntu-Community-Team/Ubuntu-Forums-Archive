---
title: "libpng-dev packages not downloading!"
date: 2006-08-16
forum: Packaging and Compiling Programs
---

### Post by redmarshall on 2006-08-16
I am Very new to Linux and probably shoudn't be messing with all this programming crap.  But I am.  I hope that I am just dumb and this is an easy fix!

I am trying to Compile Mplayer with all the new Codecs so that when I install it, it will work with "wmv" files.  found instructions on how to do it under the "how to" section of this site.(seemed simple enough, Cut and paste with a few updates)  So i get to the point where i type in... 

#./configure --enable-gui

...Everythign is going well and then I get hit with an error saying I need "libpng-dev packages" in order to compile it.  (ref. screenshot, large window on bottom)

so I try downloading...

#sudo apt-get install libgtk1.2-dev

...Nothing.  I know thats an older version but I have tried every version.  both in terminal and in Synaptic Package Manager.  I'm completely stuck.  Any Advice would be great.](*,)

---

### Post by pdub on 2006-08-16
Try doing:

**aptitude search libgtk** and see what is available. Then install the package by its proper name.

(Edit) Sorry, I see that you are installing the proper package but it has un-met dependencies.

I did not complile mplayer and I can play wmv files no problem. You can follow this guide to help setup muiltimedia and other useful things in Dapper.

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by mlind on 2006-08-17
Does this work for you?
```

sudo aptitude install libpng-dev

```

---

### Post by redmarshall on 2006-08-17
yeah, that worked great.  Thanks.  I'm really new so i'm curious,  what is aptitude?  I guess what does it stand for?

---

### Post by mlind on 2006-08-19
> **redmarshall said:**
> yeah, that worked great.  Thanks.  I'm really new so i'm curious,  what is aptitude?  I guess what does it stand for?

aptitude is like enhanced apt-get. These both are text based interfaces for Debian package management system which Ubuntu uses too.
for aptitude's manual, type **man aptitude**.

---

