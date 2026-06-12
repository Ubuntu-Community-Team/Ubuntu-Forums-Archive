---
title: "Removing Ubuntu from Computer"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Julia Dawn Mason on 2008-07-16
How do I remove the Ubintu system from my computer? Many of the programs I use will not open or run in Ubuntu.  My record keeping program for my daylilies will not run at all. I need to remove Ubuntu completely and go back to Windows XP.

---

### Post by fatality_uk on 2008-07-16
How did you install it? Was it via WUBI, or did you install onto a new partition? Once we know that, we can help you remove it.

---

### Post by coffeecat on 2008-07-16
Do you need to reinstall Windows, or did you set up a dual-boot?

If the first, just reinstall Windows - it will reformat the drive, effectively erasing Ubuntu.

If the latter, you can reformat the Ubuntu partitions, but more importantly you have to repair the mbr (master boot loader). If this is the case post back and someone will help you.

---

### Post by Julia Dawn Mason on 2008-07-16
I installed Ubuntu from I CD I received from the Ubuntu site that I had ordered it from. I installed it over Windows XP Pro I did not partition. Just how to do I go about restoreing the master boot loader?

---

### Post by carandraug on 2008-07-16
If you installed Ubuntu *over* windows then the windows you had before is lost.

You don't need to remove Ubuntu you just need to install Windows which will gladly get you rid of any other OS he finds. Like coffecat said[quote=coffecat]If the first, just reinstall Windows - it will reformat the drive, effectively erasing Ubuntu.[/quote]

---

### Post by Julia Dawn Mason on 2008-07-16
I realize that Windows was wiped out  when I installed the Ubuntu. I have the CD for Windows but it will not boot from the CD even when I go into the Boot Menu and set it for booting from the CD. I tried that and it just set there showing it was gathering information but didn't .

---

### Post by coffeecat on 2008-07-16
> **Julia Dawn Mason said:**
> I installed it over Windows XP Pro I did not partition. Just how to do I go about restoreing the master boot loader?

That's OK then. If you installed Ubuntu as the only OS on the hard drive, when you go to reinstall Windows it will reformat the whole drive (erasing Ubuntu) and it will reinstate the mbr, so you don't have to worry about the mbr. Just post back if you run into any problems

It's only when you set up a Windows/Linux dual-boot that the mbr becomes an issue if you want to get rid of Linux.

---

### Post by coffeecat on 2008-07-16
> **Julia Dawn Mason said:**
> I have the CD for Windows but it will not boot from the CD even when I go into the Boot Menu and set it for booting from the CD.

Do you mean the BIOS menu? Have you set up the BIOS to boot from the CD first?

---

### Post by carandraug on 2008-07-16
> **Julia Dawn Mason said:**
> I realize that Windows was wiped out  when I installed the Ubuntu. I have the CD for Windows but it will not boot from the CD even when I go into the Boot Menu and set it for booting from the CD. I tried that and it just set there showing it was gathering information but didn't .
If the problem is when loading from the Windows CD, maybe the problem is with the cd. From what you tell us, it starts gathering information (which seems action from the Windows CD) and then nothing happens. I may be wrong but I doubt that's Ubuntu or Linux's fault. You can try run ```
badblocks -v /dev/cdrom
```in the terminal (in Ubuntu) to check if the cd looks ok.

---

### Post by coffeecat on 2008-07-16
> **Julia Dawn Mason said:**
> I tried that and it just set there showing it was gathering information but didn't .

Another thought, Julia. It sounds as though the Windows CD is booting but then hanging for some reason. First thing it does (iirc) is to check the hard drive over. It will have detected the two (probably) Linux partitions but because these are formatted with filesystems Windows doesn't understand, it may be either hanging or just taking an awful long time to make up its mind what to do. The few times I've installed Windows, I've always formatted the HD with a Windows filesystem first and not had this problem.

So - an idea for you, if you want. Boot up with the live Ubuntu CD (yes, the CD, not from the hard drive). When you get to the desktop, go to System > Administration > Partition Editor. The partition editor will probably show you two partitions, a large ext3 one and a small swap one. Delete them both, or all and any partitions shown, until the whole hard disc is showing as unformatted or unallocated - whatever the description is. Now create one partition covering the whole hard disc, and for filesystem choose NTFS. You have to click on Apply once you've made your choices.

Now shut down and reboot with the Windows CD. With the whole hard drive formatted the way Windows likes it, hopefully the installer will now do its work.

---

