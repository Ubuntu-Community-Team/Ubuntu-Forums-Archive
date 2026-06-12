---
title: "Windows Modify GRUB's menu.lst"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by john.hall on 2008-07-26
I want both Windows and Linux to be able to modify menu.lst from a script.  Right now, it's in /boot on the Linux partition.  I would like to be able to do this without installing any kind of ext3 drivers for Windows.  

I have a FAT32 partition, and I would like GRUB to read menu.lst from that partition instead of from the ext3 partition.  Is this possible?

---

### Post by rockerphil on 2008-07-26
unfortunately i don't think that's possible since Linux uses ext2 and ext3 formats for it's partitions, which Windows can't read, sorry, you'll have to modify your GRUB list from Linux

edit: also,from what i understand GRUB is installed to your MBR, and i don't know if it's possible to move it to your FAT32 partition

---

### Post by eightmillion on 2008-07-26
This [thread]("http://lists.gnu.org/archive/html/bug-grub/2004-03/msg00047.html") seems to go into some details on what you're talking about.

---

### Post by northern lights on 2008-07-26
> **rockerphil said:**
> edit: also,from what i understand GRUB is installed to your MBR, and i don't know if it's possible to move it to your FAT32 partition
Goodness gracious, you can't move GRUB from the mbr.

However, you can access /boot/grub/menu.lst from Windows. It's just that Windows does not read ext3 out of the box. Check out [fs-driver]("http://www.fs-driver.org/"), that'll make your Linux partitions readable in Windows.

---

### Post by caljohnsmith on 2008-07-26
> **northern lights said:**
> Goodness gracious, you can't move GRUB from the mbr.
Actually, that's not true, because Grub can reside in the boot sector of a particular partition for example, and then it makes it possible to boot that partition using the "chainloader" notation in menu.lst. And of course you can always overwrite Grub in the MBR with some other boot loader like Windows XP (cough, cough). :)

John.hall, I believe that Grub has native support for FAT partitions:
[http://www.gnu.org/software/grub/manual/html_node/Features.html](http://www.gnu.org/software/grub/manual/html_node/Features.html)
That means that you should be able to create a FAT partition and install all the Grub files there (i.e. that's where menu.lst would be located then). I've never done it, but I believe it's possible.

---

### Post by northern lights on 2008-07-26
Aight. You can indeed install GRUB on the boot (first) sector of any partition. How cool is that? Never knew.

> **caljohnsmith said:**
> and then it makes it possible to boot that partition using the "chainloader" notation in menu.lst
However, it's not the "notation". If, for whatever reason, you'd want GRUB to reside in an OS' native environment, i.e. on a non-first partition or drive and not in the MBR, it needs to be chainloaded from another bootloader that _does_ reside in the MBR. [reference]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively")

Man GRUB is quite powerful.

[EDIT]
Nonetheless, it'd be much more sensible to just make Windows read ext3, if you must edit 'menu.lst' from Windows...
[/EDIT]

---

### Post by caljohnsmith on 2008-07-26
> **northern lights said:**
> Aight. You can indeed install GRUB on the boot (first) sector of any partition. How cool is that? Never knew.


However, it's not the "notation". If, for whatever reason, you'd want GRUB to reside in an OS' native environment, i.e. on a non-first partition or drive and not in the MBR, it needs to be chainloaded from another bootloader that _does_ reside in the MBR. [reference]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively")

Man GRUB is quite powerful.

That's exactly what I was alluding to :), I should have elaborated: if for instance you have more than one linux distro on one HDD, say Distro A and Distro B, you can have one linux distro install Grub to the MBR (say Distro A), and then Distro A will have control over the menu.lst at boot time. Now of course you could add Distro B to the menu.lst of Distro A using the "kernel" and "initrd" etc. notation, but it's not always easy figuring out the correct options (e.g. "ro", "quiet", "splash", etc) for Distro B. An easier way is to let Distro B install Grub to its partition's own boot sector, let it create its own menu.lst with all the correct options, and then in Distro A's menu.lst you can use the chainloader notation to boot Distro B. It's a really easy way to install multiple distros to one HDD and not have to fuss to get them to boot correctly. :)

---

### Post by northern lights on 2008-07-26
> **caljohnsmith said:**
> It's a really easy way to install multiple distros to one HDD and not have to fuss to get them to boot correctly
Yeah, that is a pain in the butt (you can't say ***, see). That's exactly why I thought this was a wonderful feature indeed.

---

