---
title: "Hardy Heron Boot Time"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by seamustry on 2008-04-24
I've just installed Hardy and I noticed that it boots up a LOT slower than 7.10...is that a known issue? 

The thing is, my Vista install boots up faster and that's saying something...

any help is appreciated!

---

### Post by ElTimo on 2008-04-24
try this:

when the Grub menu comes up, highlight the entry for Ubuntu and press 'e'
then go to the second line in the following menu and press 'e' again
add to the end of the line the word "profile"
then press enter, then 'b'
this will make your boot time slower when you do this initially, as the computer is searching for the drivers it needs to start up, but after that, it will be MUCH faster.

Also, if you have a dual-core processor, you can type in a terminal```
sudo kate /etc/init.d/rc
```and change the line that says```
CONCURRENCY=none
```to```
CONCURRENCY=shell
```

hope this helps

---

### Post by spiderbatdad on 2008-04-24
[http://ubuntuforums.org/showthread.php?t=745093](http://ubuntuforums.org/showthread.php?t=745093)

---

