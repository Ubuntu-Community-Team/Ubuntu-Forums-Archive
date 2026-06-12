---
title: "I cannot connect to any network, wired and otherwise!!"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by rufus muturi on 2012-06-13
I am running Ubuntu 12.04 Precise Pangolin. My ethernet adapter is not working but my wireless one was, until I installed wicd. Now, it does not even detect any net work and gives me the error: The system network services are not compatible with this version. I need help with this please.......

---

### Post by sanderj on 2012-06-13
Hmmm ... let me think ... you asked network questions in [http://ubuntuforums.org/showthread.php?t=2001602](http://ubuntuforums.org/showthread.php?t=2001602), you did get advice from others, but you did not reply to that ... and now you start another thread on network stuff.

So ... no, I won't help you ...

---

### Post by rufus muturi on 2012-06-14
I'm sorry about that oversight, sanderj. It won't happen again. Thank you for pointing that out and for the ipv6 links.

---

### Post by sanderj on 2012-06-15
Boot the Ubuntu 12.04 CD/USB-stick, see if Wifi works again, and if so, do a fresh install (and do not install wicd).

EDIT:

Run "sudo lshw -C network" in your current non-working setup, after booting the live-CD, and after installing the fresh Ubuntu. It will tell you which driver is used (or not) for your network hardware.

---

### Post by rufus muturi on 2012-06-18
Thank you , sanderj. I will let you know how it goes.

---

