---
title: "Question about grub and triple boot"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Mr Pockets151 on 2008-05-31
I have XP on hsda1 and Mandriva on hhda1.  I set aside another partition on the Mandriva hdd, to load Ubuntu.  Question is what happens to GRUB.  Will the Ubuntu overwrite the Mandriva GRUB?  Can I bypass the GRUB portion for ubuntu and edit the MAndriva GRUB instead?

---

### Post by wolfen69 on 2008-05-31
ubuntu will handle everything automatically. when ubuntu is done installing, you will have the choice to boot into whatever you want.

> Can I bypass the GRUB portion for ubuntu and edit the MAndriva GRUB instead?yes, if you use the alternate cd of ubuntu.

---

### Post by Mr Pockets151 on 2008-05-31
okay.  I just happen to like the grub screen on mandriva better.

---

### Post by meierfra. on 2008-05-31
I recommend installing Grub to the boot sector of your Ubuntu partition:

[http://ubuntuforums.org/showthread.php?t=810546#13]("http://ubuntuforums.org/showthread.php?t=810546#13")

This will let you use your mandriva Grub menu, but you won't have the edit your mandriva menu.lst every time Ubuntu has a kernel update.


To install grub  to the ubuntu partition, click on the advanced button in step 7 of the Installation with the LiveCD

---

### Post by Joeb454 on 2008-05-31
> **wolfen69 said:**
> <quote snipped>

yes, if you use the alternate cd of ubuntu.

You can do it from the Desktop (Live) CD as well, there's an "advanced" option in the bottom right of ubiquity before you tell it to install. They are the GRUB options :)

---

### Post by Mr Pockets151 on 2008-05-31
> **meierfra. said:**
> I recommend installing Grub to the boot sector of your Ubuntu partition:

[http://ubuntuforums.org/showthread.php?t=810546#13]("http://ubuntuforums.org/showthread.php?t=810546#13")


To install grub  to the ubuntu partition, click on the advanced button in step 7 of the Installation with the LiveCD

The ubuntu GRUB or the Mandriva GRUB.  Or doesn't matter?  Whatever I choose.

---

### Post by meierfra. on 2008-05-31
Install the Ubuntu Grub to the Ubuntu partition.  This can be done during step 7 of the installation. Click on the advanced button and fill in the location of you ubuntu partition.

---

### Post by Mr Pockets151 on 2008-05-31
Nice!  Thanks.

---

### Post by meindian523 on 2008-05-31
and after installing Ubuntu grub to Ubuntu partition,make sure to **chainload** Grub from the Mandriva Grub.

---

### Post by Mr Pockets151 on 2008-05-31
So something like (in my case)

title Ubuntu
root (hd0,2)       
chainloader +1

Partitions are numbered starting at 1 right? I got a back-up of my menu.lst in any case.

---

### Post by meindian523 on 2008-05-31
Nopes,partitions are numbered from zero.And you have Windows installed too,so I guess chainloader +1 would have been taken up there.So you need chainloader +2.

---

### Post by Mr Pockets151 on 2008-05-31
okay, so yeah I will use +2.  Anyway, I have enough responses.  It's gonna be simple.  :popcorn:

---

### Post by meierfra. on 2008-05-31
It's always "chainloader +1". Only the "root (hd?,?)" varies. Grub starts counting at 0. The first number is the hard drive, the second the partition.

Post the output of "fdisk -l" if you need help with  numbers.

---

### Post by meindian523 on 2008-06-02
Are you sure?

---

### Post by meierfra. on 2008-06-02
> Are you sure
Yes.

"chainloader +2" would mean that you are trying to boot from the second **sector** of a partition.  Nobody puts the booting information on the second sector, it always starts on the first sector.


Edit:  Correction : chainloader +2 means " read the first two sector of the root partition, starting at the beginning. So probably chainloader +2 will work under most circumstances, but  it is  still best to use "chainloader +1" to boot Vista or XP.

---

### Post by housam on 2008-06-02
You can read this guide about maintaining a [[COLOR="Red"]_multi-boot _[/COLOR]]("http://ubuntuforums.org/showthread.php?t=724817")on your system.

---

