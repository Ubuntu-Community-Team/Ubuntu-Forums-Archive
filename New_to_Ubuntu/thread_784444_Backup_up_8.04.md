---
title: "Backup up 8.04"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by noiseordinance on 2008-05-06
Ok, so I'm curious about the best way to backup 8.04. Here's the scenario: I have two partitions... XP and Ubuntu 8.04. Once I get Ubuntu set up nicely, I'd like to make a disaster recovery disk since Ubuntu likes to break when I experiment with simple things like startup manager and whatnot. How can I create a way to easily reinstall 8.04 with all my settings, and without overwriting XP or any partition info?

---

### Post by twright on 2008-05-06
you could use rsync

sudo rsync /home /(whereever the backup is)

if you put /home on a separate partition that might help (but backup as well)

---

### Post by sdennie on 2008-05-06
The other option would be to do your experiments in a virtual machine before trying them on your real machine to make sure they are safe.  There are many different VM options including virtualbox and virt-manager.

---

### Post by Tatty on 2008-05-06
Try: [http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

I have heard good things about partimage, although never used it myself.

---

### Post by mapes12 on 2008-05-06
This is not good practice. If you loose windoze you will have to reinstall it and then have any issues about the 120 day limit on activation. To play around with Linux then use another drive or better still a base unit with a KVM to use existing keyboard, mouse and monitor. See here about the safe way to play:

[http://www.aboutdebian.com/linux.htm](http://www.aboutdebian.com/linux.htm)

---

