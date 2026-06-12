---
title: "format ubuntu hard drive"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by newport_j on 2012-04-09
I want to format my laptop hard drive, wipe it clean and re install Ubuntu. The only thing that I need to know is how to format the hard drive.

I realize everything will be lost. That is why I am backing up the important things.

What is the command to format a hard drive?

Thanks in advance.

Newprt_j

---

### Post by Bucky Ball on 2012-04-09
You don't really need to do this prior to install. When you get to the partitioning section of the install, choose 'Something Else' and manually setup the partitions you want. In there you can delete existing partitions then start over. All part of the install ...

---

### Post by Penguinnerd on 2012-04-09
EDIT: Oops, someone beat me to it...


When you do the installation, the installer can format it automatically for you.

And with the backups, the old saying "Measure twice, cut once" applies. Double and triple check that you're not leaving anything behind. There's nothing worse than lost data. That's my $0.02.

And, good luck! :)

---

### Post by Bucky Ball on 2012-04-09
> **Penguinnerd said:**
> When you do the installation, the installer can format it automatically for you.



That is another option. But I don't like the way Ubuntu automatically sets things up as I like a separate /home partition, like so:

/
/home
/swap

;)

---

### Post by Bizobinator on 2012-04-09
A quick question along these lines:

I installed Ubuntu on my entire hard drive.  I'd like to dual boot Windows 7 and Ubuntu.  

In order to do that, would I have to re-install Ubuntu?  Or, can I just install Windows 7 and have it over-write part of the Ubuntu partition?

---

### Post by d4m1r on 2012-04-09
Typically you should:

1) Install Windows
2) Install Ubuntu

Because the Windows boot manager (MBR) will overwrite GRUB if you install Ubuntu first. If you want to proceed by (re)installing Ubuntu first you would have to:

1) Install Ubuntu
2) Install Windows
3) Rebuild GRUB

---

### Post by Bucky Ball on 2012-04-10
> **d4m1r said:**
> Typically you should:

1) Install Windows
2) Install Ubuntu

Because the Windows boot manager (MBR) will overwrite GRUB if you install Ubuntu first. If you want to proceed by (re)installing Ubuntu first you would have to:

1) Install Ubuntu
2) Install Windows
3) Rebuild GRUB

Ubuntu is already installed on the entire drive.

Boot from a LiveCD, 'Try Ubuntu', when at a desktop open Gparted;
Shrink the Ubuntu partition *leaving free space at the beginning of the drive *(Windows wants to be on first drive, first partition);
Install Windows using the free space you created at the beginning of the drive;
Reinstall grub (research this but you may be able to use Boot Repair from the LiveCD - yes, it will install and work using the LiveCD)

Done.

You need to search for clues here; there are a lot of how-tos ... ;)

[http://au.search.yahoo.com/search?p=install%20windows%20after%20ubuntu&fr=altavista&fr2=sg-gac&pqstr=install%20windows%20after%20ubu]("http://au.search.yahoo.com/search?p=install%20windows%20after%20ubuntu&fr=altavista&fr2=sg-gac&pqstr=install%20windows%20after%20ubu")

ESPECIALLY check this:

[http://members.iinet.net.au/~herman546/](http://members.iinet.net.au/~herman546/)

... and this:

[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

Super Grub Disk can help with all sorts ... Good luck ...

---

