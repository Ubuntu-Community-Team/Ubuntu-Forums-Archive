---
title: "Another autologin how to"
date: 2006-11-20
forum: Outdated Tutorials &amp; Tips
---

### Post by kerry_s on 2006-11-20
1

---

### Post by VileTimes on 2007-04-24
Just a note for anyone trying to get this autologin method working in Feisty, follow all of the steps as per an Edgy install with the exception of editing the tty1 file. Instead of adding a line like this:

```
respawn /sbin/getty -n -l /usr/bin/autologin 38400 tty1
```


... make sure your edit looks like this:

```

respawn

exec /sbin/getty -n -l /usr/bin/autologin 38400 tty1
```

Here is my tty1 file in its entirety:

```

# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system
start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

stop on shutdown

respawn

exec /sbin/getty -n -l /usr/bin/autologin 38400 tty1

```

Thanks again for the howto and I hope this helps someone.

---

### Post by xi0n0ix on 2007-06-13
Hello,

Great tutorial! Worked like a charm!

I was just wondering, how would I automatically start a program (PD for example) after auto startx completes... 

So when I (re)boot the system I am automatically logged in, X automatically starts, and then my program automatically starts and runs..

Do I just add a line at the bottom of my ~/.profile like 'exec pd' or do I need more to make sure that X is started properly and has finished.

thanks
mark

---

### Post by ways on 2007-06-18
> **xi0n0ix said:**
> Hello,

Great tutorial! Worked like a charm!

I was just wondering, how would I automatically start a program (PD for example) after auto startx completes... 

So when I (re)boot the system I am automatically logged in, X automatically starts, and then my program automatically starts and runs..

Do I just add a line at the bottom of my ~/.profile like 'exec pd' or do I need more to make sure that X is started properly and has finished.

thanks
mark

you add the program name and an '&' in ~/.xprofile

```
gaim &
```

---

### Post by regomodo on 2007-07-08
something is wrong with this "howto". It works fine until i reboot where tty1 hangs at 

# running local bootscripts (etc/rc.local)

I have to get into tty2 and then login, thus rendering the autologin procedure useless.

---

### Post by kerry_s on 2007-07-08
now a days you should use gdm, it use's less resources and everything is so tied into a login manager, that when you don't use one you get all these little quirks/errors that continue to build up. i've run several tests and with gdm it use's less resources then startx, i have no idea why.

---

### Post by VileTimes on 2007-07-08
> **regomodo said:**
> something is wrong with this "howto". It works fine until i reboot where tty1 hangs at 

# running local bootscripts (etc/rc.local)

I have to get into tty2 and then login, thus rendering the autologin procedure useless.

I was experiencing the same issue until I changed the tty1 file.

Did you try what I wrote in my reply up above?

---

### Post by regomodo on 2007-07-09
> **VileTimes said:**
> I was experiencing the same issue until I changed the tty1 file.

Did you try what I wrote in my reply up above?

@ viletimes - no i didn't see yours. I'll give it another try. Cheers for the heads up

---

### Post by jkat on 2007-09-03
Excellent article.  One small error, though, in the *inittab* changes for Dapper: a colon is needed after *respawn*, ie.

```
1:2345:respawn /sbin/getty -n -l /usr/bin/autologin 38400 tty1
```

should be

```
1:2345:respawn:/sbin/getty -n -l /usr/bin/autologin 38400 tty1
```

Otherwise at boot  *init* responds with errors of the action field being too long.

---

### Post by UmbraMalison on 2007-12-05
Hi,

i just can't get this to work on my machine.

im using feisty fawn, and i took note of VileTimes' tty information. but to no avail.

i've read and re-read the entire post. but perhaps there is something i keep missing.

my error is:

init: tty1 main process (3279) terminated with status 1

the tty1 is completely dead, i have to change to tty2 to do anything.

Has anyone else seen this before? perhaps some recent updates has caused my machine to behave differently to the fesity fawn that VileTimes used??

any help would be great, thanks

---

### Post by UmbraMalison on 2007-12-10
if you have problems getting this to work like i did. See this post where ive described the solution i used.

[http://ohioloco.ubuntuforums.org/showthread.php?p=3926755#post3926755](http://ohioloco.ubuntuforums.org/showthread.php?p=3926755#post3926755)

---

