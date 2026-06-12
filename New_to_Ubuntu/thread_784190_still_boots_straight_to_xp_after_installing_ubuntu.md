---
title: "still boots straight to xp after installing ubuntu 8"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by yaque on 2008-05-06
I have an existing Windows XP home installation on one HD.
I installed ubuntu 8 on a separate HD.
(I think) I set it to dual boot during installation. 
(Or maybe not)

It boots up directly to Windows without going thru a dual boot screen.
How can I get it to dual boot?

It's an Athlon 3100 with 512 mb RAM and 2 HD
1st is 14 gb IBM with the Windows XP installation and the
2bd is  8 gb  WD with the new ubuntu installation

---

### Post by Hospadar on 2008-05-06
you probably need to change (in your bios) the first boot hard drive.  My guess is that the ubuntu boot loader is installed where you installed ubuntu, and the bios isn't even looking there.

During bootup, before windows or linux anything look for some options like "<F12> to enter setup" and get into your setup and re-order your hard drives in the boot order to put the linux one first.

If you don't see any options like that, you can try doing what I do at work, and holding down all the F keys as well as backspace and delete during boot.

Generally though, it's either F2, F10, F12, backspace or delete to get into the boot menu, then look for something like "Boot Options" or "Advanced Bios Features" if in doubt, you can just look through every option until you find the boot order, it'll probably be called "Hard Disk Boot Order" or something.

---

### Post by Michl on 2008-05-06
[HTML]https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs[/HTML]

[HTML]http://www.ehomeupgrade.com/2006/06/02/how-to-dual-boot-ubuntu-606-dapper-linux-desktop-along-side-windows-xp/[/HTML]

The second one says it's for Dapper, but it works for any
ubuntu distro.

The best way to do it is to put ubuntu on your master, windows on
the slave and fool windows to think it is the master.

Normally, when you do a fresh install of Ubuntu with the windows hard drive still plugged in, Ubuntu automatically detects the other hard drive and Grub will automatically list it as a choice at startup.  So I'm not sure what you did.  Maybe you unplugged the NSTF hard drive during installation?

---

### Post by mapes12 on 2008-05-06
Sorry if I'm stating the blindingly obvious but backup any critcal data and settings either on your windoze drive or Linux drive before messing with the Grub boot loader and your Master Root Record (MBR). Tip: back up the MBR as well.

Lesson learnt from experience..................

---

### Post by yaque on 2008-05-06
Replying to Hospadar:

Bingo! that did it. Thanks! This forum is great!

(Yes I backed up everything to my new computer:
 Athlon dual core, 2 gb RAM, 160gb HD, etc.
which I hope to migrate too when I get the hang of linux.)

the last poster:
Good nag, backup should ALWAYS be mentioned, anybody can forget.

---

