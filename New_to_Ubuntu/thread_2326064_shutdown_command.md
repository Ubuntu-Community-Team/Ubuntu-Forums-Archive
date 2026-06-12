---
title: "shutdown command"
date: 2016-05-28
forum: New to Ubuntu
---

### Post by boz_1812 on 2016-05-28
Hi,

I'm using the shutdown command in a crontab (bad idea I believe - but it works for me).  I've read through the man pages and various web pages, but still can't get my head around the difference between the -h and -P options.
I want the pc to shutdown cleanly and power-off, so I'm using -P.
What does -h (halting the system) actually do differently?
Thanks.

---

### Post by izznogooood on 2016-05-28
I believe the information you seek can be found here:
[http://www.computerhope.com/unix/uhalt.htm](http://www.computerhope.com/unix/uhalt.htm)

 halt:
If you are logged in as root, issuing the halt command will cease all CPU function on the system. On most systems, this will drop you into single-user mode and then power off the machine.


poweroff:
If you are logged in as root, issuing the poweroff command will send an ACPI hardware signal which will instruct the system to commence with a complete and immediate shutdown. This is roughly equivalent to pressing the power button on a typical desktop computer.

FYI: I've always used the "shutdown -h" cmd.

---

### Post by wildmanne39 on 2016-05-28
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

### Post by boz_1812 on 2016-05-29
Excellent.  Thanks for the information.

---

### Post by vasa1 on 2016-05-29
> **boz_1812 said:**
> Hi,

I'm using the shutdown command in a crontab (bad idea I believe - but it works for me). ...
But you must have a good reason for doing so. Mind sharing? :)

---

### Post by boz_1812 on 2016-06-02
Sure.  This pc lives in my garage and is not used overnight, so rather than go out in the cold to shut it down, I use the cron (so I don't forget), then a timer to turn off all attached equipment and save some power.  Also, if the power is not turned off, the wake on lan option on the motherboard causes this pc to start a boot cycle (runs about 2 seconds) every 10 minutes or so.  A minor annoyance, but I haven't been able to figure out if that can be stopped.
Cheers.

---

### Post by QLee on 2016-06-02
> **boz_1812 said:**
>  Also, if the power is not turned off, the wake on lan option on the motherboard causes this pc to start a boot cycle (runs about 2 seconds) every 10 minutes or so.  A minor annoyance, but I haven't been able to figure out if that can be stopped.
Cheers.

Probablly going to depend a little on how old the MB is. Maybe a BIOS option for WOL or with some older (and perhaps some newer) MBs there is a WOL jumper that extends the standby voltage to the NIC card to allow WOL. That jumper is usually open by default  but yours may have been installed at some point, if there is one.

---

