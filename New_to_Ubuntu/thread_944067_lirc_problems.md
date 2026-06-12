---
title: "lirc problems"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Nephus on 2008-10-10
I just received an iguanaworks IR transceiver today and I can't get lirc to work properly.

I can get it to receive just fine using igclient --receiver-on    --sleep 100 per the installation instructions at [http://iguanaworks.net/projects/IguanaIR/wiki/GettingStarted](http://iguanaworks.net/projects/IguanaIR/wiki/GettingStarted) so it appears that the device works and is configured correctly.  What I cannot get to work is lirc.

here's an example:
```

nephus@muse:~$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                                     

nephus@muse:~$ mode2
mode2: error opening /dev/lirc
mode2: No such file or directory
nephus@muse:~$ sudo irrecord test

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)


```

I installed lirc using apt-get install lirc then configured it via the screens that popped up afterwards, but I can't get irrecord or mode2 to work.  I also can't get it to send anything either (as confirmed by looking at the led through a digital camera).

What am I doing wrong?

---

### Post by Nephus on 2008-10-11
well, found out why it wasn't working, the version that installs with apt-get doesn't include support for iguanaIR even though it lets me select the device during install.  So, I tried to manually build a version that did.  Now I've got a half install that I can't find and /etc/init.d/lirc start doesn't do anything.  half the commands aren't found, but if I use sudo they run for some odd reason.  I'm really pulling my hair out here, does anyone have some advice?

---

### Post by Nephus on 2008-10-11
ok, new status update in case anyone has any advice from this point on.  Figured out what's wrong when I use make to build from source. It's installing everything in /usr/local/bin and usr/local/sbin instead of usr/bin and usr/sbin.  That's the main reason why nothing is working properly from what I can tell. It just keeps saying command not found whenever I try to run anything. How do I get it to stop doing that?

---

### Post by rbm0307 on 2008-10-12
> **Nephus said:**
> It just keeps saying command not found whenever I try to run anything. How do I get it to stop doing that?
Try adding /usr/local/bin;/usr/local/sbin  ahead of /usr/bin and /usr/sbin to the PATH variable in /etc/profile.  This path will be exported to all environments.

---

### Post by jfacemyer on 2008-10-31
According to [this bug]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/153457"), compiling according to directions should work, but for me, following the directions didn't get me anywhere (as you can see from the bug comments).

Anyone have any ideas about how to get LIRC to compile in such a way that I can have Iguana support *and* keep a relatively clean system (using .debs)?

---

### Post by jfacemyer on 2008-11-22
Heck, I'd be happy to get any response from anyone - even one that says, "Dude it'll never work because its sole purpose is to frustrate you".  I'd even be happy with that.

But it would be better to get some real help :)

---

### Post by srmcatee on 2009-01-31
K, the driver is missing.

I found a debian lrc package that is compiled and has the iguana driver available.

You can download it here: [http://iguanaworks.net/downloads/lirc_0.8.3-0ubuntu2_i386.deb](http://iguanaworks.net/downloads/lirc_0.8.3-0ubuntu2_i386.deb)

However, this package looks for the lirc  device as /dev/lirc.  Ubuntu maps it as /dev/lirc0.

I'm still digging to figure this one out.

---

### Post by srmcatee on 2009-01-31
Sorry, I did not do a complete post.

To get the error i did an sudo lircd -n

I got the following:
lircd-0.8.3[6119]: lircd(userspace) ready
lircd-0.8.3[6119]: accepted new client on /dev/lircd
lircd-0.8.3[6119]: could not get file information for /dev/lirc
lircd-0.8.3[6119]: default_init(): No such file or directory
lircd-0.8.3[6119]: caught signal
Terminated

The only device I have is /dev/lirc0

---

