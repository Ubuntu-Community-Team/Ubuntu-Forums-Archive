---
title: "frequency out of range again"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by nitromorz on 2013-02-03
Oh dear, 'Frequency out of range' is back again. 
I had this issue a year or so ago and then it was solved by editing out the # in /etc/default/grub   to:     GRUB_GFXMODE=640x480

I thought maybe the last headers update had reset this entry somehow but having gained access using 'System Rescue CD' to check this, it was as it was supposed to be, sans #.

Update to Linux 3.2.0-37-Generic-Pae       February Friday 1st 

Tried: un-commenting #GRUB_TERMINAL=console
Also 'Boot Repair'. URL generated          [http://paste.ubuntu.com/1604185/](http://paste.ubuntu.com/1604185/)
No joy.

OS = Ubuntu 12.04 Precise  LTS monitor multi-desktops, 1440x900 native 
640x480 no longer works.

At the moment I am working with the Daniel Richter 'grub customizer' to test a whole series of offered resolutions  to allow the grub to engage. Nothing yet.

So I am wondering if anyone else has this issue with the last update of headers?
Also if anyone can suggest a fix and/or is it time to jump ship?

NB slow talk at my age ;)

---

