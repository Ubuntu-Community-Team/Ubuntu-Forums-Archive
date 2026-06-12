---
title: "sudo dpkg --purge linux-image-3.2.0-36-generic hangs"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by psilva261 on 2013-01-18
Now I called

sudo dpkg --purge linux-image-3.2.0-36-generic

It hanged at: Found memtest86+ image: /boot/memtest86+.bin

So I did CRTL+C.  Anyhow, apt-get is now willing to be called again.  Eventhough it complains that

inux-image-server : Depends: linux-image-3.2.0-36-generic but it is not going to be installed

I wonder whether I should try a distribution upgrade...  (+ I wonder what would happen if I rebooted now ;))

---

### Post by ibjsb4 on 2013-01-18
@psilva261

Your problem is not the same as the OP's, with the 3.5 kernel.  To minimize confusion  I suggest starting your own thread.

---

### Post by psilva261 on 2013-01-18
Hi ibjsb4,

Sure, but the problem exists since years so odds are low it depends on the Kernel version.  (The oldest blog/forum post I found about this issue is from 2008.)

Philip

---

### Post by psilva261 on 2013-01-18
Or maybe it does depend on the kernel version but the cause is basically a script that has problems with some kernel versions...
(Didn't mean to be offensive by the way)

---

### Post by s.fox on 2013-01-18
Please do not hijack other peoples threads.

Posts moved to own thread.

---

### Post by psilva261 on 2013-01-18
Anyway, I think I've solved it:

Afterwards I did sudo apt-get update, sudo apt-get -f upgrade, killed it again.  Then in /var/lib/dpkg/info/linux-image-3.2.0-36-generic.postrm I commented lines 326-332.  And then I set update_initramfs=no in /etc/initramfs-tools/update-initramfs.conf (tried this before, but this didn't work without the trick to comment the lines above.)  Then I ran sudo dpkg --configure -a and apt-get works again.

I cannot really recommend anybody to do this on a production system, but I think these script could really need some maintenance:

$ head -n 11 /var/lib/dpkg/info/linux-image-3.2.0-36-generic.postrm
#! /usr/bin/perl
#                              -*- Mode: Cperl -*- 
# image.postrm --- 
# Author           : Manoj Srivastava ( [email]srivasta@glaurung.green-gryphon.com[/email] ) 
# Created On       : Sat May 15 11:05:13 1999
# Created On Node  : glaurung.green-gryphon.com
# Last Modified By : Manoj Srivastava
# Last Modified On : Wed Sep 13 11:26:19 2006
# Last Machine Used: glaurung.internal.golden-gryphon.com
# Update Count     : 57
# Status           : Unknown, Use with caution!

---

### Post by ibjsb4 on 2013-01-18
Nothing wrong with a dist-upgrade.

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by ibjsb4 on 2013-01-18
Well, I guess the only thing left to do is ..

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by psilva261 on 2013-01-18
Ok thanks...

By the way, I realized this broken script is (almost) the same for Kernel versions 2.6.x - 3.2.x.  Didn't check 3.5.x though because I don't have a 12.10 system here.

---

### Post by psilva261 on 2013-01-18
>Well, I guess the only thing left to do is ..
>
>[https://wiki.ubuntu.com/UnansweredPo.../SolvedThreads](https://wiki.ubuntu.com/UnansweredPo.../SolvedThreads)

Are you serious? :p

---

### Post by psilva261 on 2013-01-21
And it happened again after doing sudo apt-get update ; sudo apt-get upgrade, hangs at Found memtest86+ image: /boot/memtest86+.bin

---

### Post by psilva261 on 2013-01-23
Solved

---

