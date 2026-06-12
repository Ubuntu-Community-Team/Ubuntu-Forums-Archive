---
title: "Installing XMMS via Synaptic..."
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Bakhman on 2008-09-07
I just installed the entire package plugin for XMMS2, and I am such a noob that I don't even know where the file is now. It's not under Applications.. so I assumed I had to install via terminal, with sudo apt-get install xmms, but that gave me a response like I have to check another repository or something.

Just as a general Q, where do programs go when you install them via package manager?

---

### Post by tamoneya on 2008-09-07
first of all there are two different packages: xmms and xmms2. It seems to me like you want the latter so run this:```
sudo apt-get remove xmms
sudo apt-get install xmms2
```
As for where things are installed two it isnt always an easy question because there isnt just one place.  The easiest way to find out is to run this:```
which xmms2
``` it should return something like /usr/bin/xmms2

---

### Post by Bakhman on 2008-09-08
Aight, that 2nd command is neat, I'll have to keep that in mind.
So I found a bunch of .exe XMMS2 files in my bin, but I double click them (in order to run in terminal) and nothing happens; and it is still not in the applications menu.. was there something in addition I need to do?

I really need this program because Rhythmbox keeps screwing up my sound card..

---

### Post by starcannon on 2008-09-08
If you liked xmms, you may find audacious a better replacement than xmms2; at least that was the case for me. Works great, feels like an improved version of xmms, where for me xmms2 felt like a step backwards.

just my .o2, take it at that value ;)

GL have fun.
~starcannon

---

### Post by roscal on 2008-09-08
Are you using Hardy?

XMMS is no longer in the repository.

However you can get a .deb  of the original XMMS here:
[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

---

### Post by cozmicharlie on 2008-09-08
XXMS is not available through Synaptic anymore in Hardy but you can still install it.  There is an excellent method posted in here ([http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)).  This tutorial shows how to set up flac, shn and a launcher in Hardy ([http://ubuntuforums.org/showthread.php?t=833164&highlight=shn](http://ubuntuforums.org/showthread.php?t=833164&highlight=shn)).  It is a lot of command line but if you just cut and paste each command as written it works great.

---

### Post by Bakhman on 2008-09-09
Ah, that must have been the problem ~~ I was using Hardy.
Well, Audacious is indeed better, I think I can stick with this! Thanks!

---

### Post by roscal on 2008-09-09
Download XMMS compiled for Hardy here:

[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

You want the .deb file.
Works like a charm in Hardy.
:)

---

