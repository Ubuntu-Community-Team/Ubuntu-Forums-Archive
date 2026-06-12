---
title: "Installation help!"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by bloodymind on 2008-11-14
Hello there,
I have windows XP installed on a hard drive
and I've installed ubuntu 8.10 on other hard disk in the primary partition
and after installation complete, I restart then when I boot from the Linux hard disk, I get "NTLDR missing press any key to restart"

and I've searched I found that somehow there is a solution with grub
but unfortunately I don't have a floppy disk drive,
Can anyone help me do the dual boot thing without floppy disk?
Thanx in advance

---

### Post by Chesamo on 2008-11-14
> **bloodymind said:**
> Hello there,
..::blig block o' text::..
You can use GRUBconfig. I've found that RIP is a useful boot disk for that, as it also includes partitioning and file management utilities.
[http://www.tux.org/pub/people/kent-robotti/looplinux/rip/](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/)
NTLDR is the Windows boot menu/loader tool, which is broken once Ubuntu is installed (because Ubuntu tries to install GRUB over it).

---

