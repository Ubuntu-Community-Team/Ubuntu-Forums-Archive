---
title: "accessing ubuntu files on Win XP"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by mindlessly self indulgent on 2008-11-18
Okay, I think I get the whole accessing files from windows on Ubuntu thing, but now I have a similar question... is there a way to access my Ubuntu files on Windows XP?  

I am downloading a torrent in Ubuntu (BTW, transmission is pretty nice), but now my issue is that once it's downloaded I need to get it over to Windows so I can burn it onto a DVD.

Anyway, any help is appreciated!  Thanks :)

---

### Post by w4ett on 2008-11-18
Take a look at Ext2IFS for windows.

[http://www.go2linux.org/access-ext2-ext3-from-xp](http://www.go2linux.org/access-ext2-ext3-from-xp)

---

### Post by nhasian on 2008-11-18
why cant you burn it in ubuntu? I've used the Brasero that comes built in many times and havent had any issues.  I know a lot of people recommend K3B but i havent tried that yet.  If you need to burn an ISO that has a .dvd file you can use imgburn with wine.

> **mindlessly self indulgent said:**
> once it's downloaded I need to get it over to Windows so I can burn it onto a DVD.

---

### Post by LeAstrale on 2008-11-18
You should be able to burn the ubuntu iso with either k3b (kubuntu/kde) or Brasero (ubuntu/gnome) which is the default of ubuntu. It should be very easy to spot how to burn it.

/LeAstrale

---

### Post by NewJack on 2008-11-18
> **w4ett said:**
> Take a look at Ext2IFS for windows.

[http://www.go2linux.org/access-ext2-ext3-from-xp](http://www.go2linux.org/access-ext2-ext3-from-xp)

+1  Works like a charm

---

### Post by jenkinbr on 2008-11-18
> **w4ett said:**
> Take a look at Ext2IFS for windows.

[http://www.go2linux.org/access-ext2-ext3-from-xp](http://www.go2linux.org/access-ext2-ext3-from-xp)
I +2 that.  Use it all the time, and actually have my windows 'my docs' folder set to my ext3 home volume. :)

---

### Post by SanskritFritz on 2008-11-18
A slightly lighter read-only solution, if you use Total Commander:
[http://ghisler.fileburst.com/fsplugins/ex2fs.zip](http://ghisler.fileburst.com/fsplugins/ex2fs.zip)
on this page:
[http://www.ghisler.com/plugins.htm#filesys](http://www.ghisler.com/plugins.htm#filesys)

---

### Post by egalvan on 2008-11-18
> **w4ett said:**
> Take a look at Ext2IFS for windows.

[http://www.go2linux.org/access-ext2-ext3-from-xp](http://www.go2linux.org/access-ext2-ext3-from-xp)

+3

Double-dittos on that,

 I have been using it for about a year to keep almost everything under Linux-type file-systems. Keeps my XP partition small (around 6g at this time)

I've been thinking of experimenting with this, BTW.
I plan on moving my "Program Files" and "Programs" folders to my shared Linux Partition. We'll see how XP likes that.

ErnestG

---

### Post by Keen101 on 2008-11-18
I've used this fine in the past.

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

---

