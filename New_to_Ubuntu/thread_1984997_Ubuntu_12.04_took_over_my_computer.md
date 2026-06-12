---
title: "Ubuntu 12.04 took over my computer"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by methomas on 2012-05-22
Greetings,

I installed Ubuntu 12.04 yesterday. It worked just fine, except when I went back to Windows 7, I didn't have a Windows 7.

Ubuntu had reformatted my whole 600 gig hard drive for it's self. Totally ate about 400 gig of data files which I may never recover.

I just want to get back control of my computer, reinstall windows 7 along with Ubuntu. I am going to use mostly Ubuntu but have a couple of specialized program that only run on windows.

I have spent the day trying to reformat the drive and start over.  I have tried to reformat a dozen different ways, tried to repartition, etc.

What can I do to reclaim my hard drive?

Thanks,

M E

---

### Post by wilee-nilee on 2012-05-22
> **methomas said:**
> Greetings,

I installed Ubuntu 12.04 yesterday. It worked just fine, except when I went back to Windows 7, I didn't have a Windows 7.

Ubuntu had reformatted my whole 600 gig hard drive for it's self. Totally ate about 400 gig of data files which I may never recover.

I just want to get back control of my computer, reinstall windows 7 along with Ubuntu. I am going to use mostly Ubuntu but have a couple of specialized program that only run on windows.

I have spent the day trying to reformat the drive and start over.  I have tried to reformat a dozen different ways, tried to repartition, etc.

What can I do to reclaim my hard drive?

Thanks,

M E

Probably to late for a full recovery, but don't use the HD use a live cd as of now, and wait for a user who knows tools like testdisk gives you some help.

---

### Post by PhantomTurtle on 2012-05-22
> **methomas said:**
> Greetings,

I installed Ubuntu 12.04 yesterday. It worked just fine, except when I went back to Windows 7, I didn't have a Windows 7.

Ubuntu had reformatted my whole 600 gig hard drive for it's self. Totally ate about 400 gig of data files which I may never recover.

I just want to get back control of my computer, reinstall windows 7 along with Ubuntu. I am going to use mostly Ubuntu but have a couple of specialized program that only run on windows.

I have spent the day trying to reformat the drive and start over.  I have tried to reformat a dozen different ways, tried to repartition, etc.

What can I do to reclaim my hard drive?

Thanks,

M E

Were they important files. If so stop what you are doing, and try to recover it first. If you do not care about then, wait for a user who knows tools like testdisk like wilee-nilee said. When you got everything sorted out remember to install Windows first or it will overwrite Grub and you would need to reinstall it using a live cd.

---

### Post by methomas on 2012-05-22
The data is not important.
The important stuff I can reinstall by going back over emails stored on a server.

I just want to clean the drive and reinstall windows and ubuntustudio.

M E

---

### Post by Mark Phelps on 2012-05-23
It's best to install MS Windows first -- since Ubuntu can find that and add it to your boot selection menu.

Boot from an Ubuntu LiveCD or LiveUSB, open the Gparted app, and use that to remove ALL the partitions from the drive.

Then, boot from your Win7 DVD and install it to the drive.  Let it default regarding partitions and sizes.

Once that is done, boot into Win7 and use the Disk Management utility to shrink Win7 down to make room for Ubuntu.  Do NOT use GParted to do this, as doing so risks damaging the Win7 filesystem.  Also, do NOT format the unallocated space from inside Win7.

Once that is done, you are free to install Ubuntu into the unallocated space.

---

### Post by xedi on 2012-05-23
> **Mark Phelps said:**
> 
Once that is done, boot into Win7 and use the Disk Management utility to shrink Win7 down to make room for Ubuntu.  Do NOT use GParted to do this, as doing so risks damaging the Win7 filesystem. 


This is the first time I heard it and it seems hard to believe that if this were a significant danger, that the Ubuntu installation process would offer you to install Ubuntu automatically alongside Windows 7 or do it manually (I believe with the help of gparted). I myself had never problems with that.

Edit: Or do you mean that you yourself screw up and damage the file system with gparted? In that case, it wouldn't be a huge issue because it is a new windows installation anyways and you can just choose Ubuntu to install automatically alongside windows which should be hassle free.

---

### Post by wilee-nilee on 2012-05-23
> **xedi said:**
> This is the first time I heard it and it seems hard to believe that if this were a significant danger, that the Ubuntu installation process would offer you to install Ubuntu automatically alongside Windows 7 or do it manually (I believe with the help of gparted). I myself had never problems with that.

Edit: Or do you mean that you yourself screw up and damage the file system with gparted? In that case, it wouldn't be a huge issue because it is a new windows installation anyways and you can just choose Ubuntu to install automatically alongside windows which should be hassle free.

Any partitioning has to be done while informed. There are files in windows that are basically flagged as unmovable, these can be moved though with the right partitioner. A W7 install should really be resized with its virtual partitioner, and if it limits the shrink size a specialized partitioner can move them and then it will allow a smaller shrink size.

There are standard ways to do all this, some users not the OP here choose to act with out being informed and have problems.

Gparted will just do what you tell it, an excellent app, but must be used understanding its use.

---

### Post by jmore9 on 2012-05-23
If i understand correctly you want to install win7 and then install ubuntu.

First i would get a copy of gparted live , boot from it , and make the partitons that you want for your two os to work in.

For example on my winxp / ubuntu machine i have a 320 gig hard drive (ide) and i have 50 gigs for winxp and the balance for ubuntu.  I started with an empty drive and used gparted live to fromat the drive as follows :

partition 1 - NTFS ( winxp)
partition 2 - EXT4 - (Ubuntu)
partition 3 - Linux Swap

After i get above done i boot with my windows disk and do the windows install on the NTFS partiton.  After windows is all done and installed i boot with the Ubuntu disk and install ubuntu on the EXT4 partiton.  When i install Ubuntu i use the other option and select the ext4 partition as where ubuntu should intall itself to.  I also am lazy so i put everything into / .

After Ubuntu has done its thing at the end it will install grub which i have installed to boot partiton of hda , my only drive so no where else to put it.  Then all done just tweating windows and Ubuntu OS's to where it want them.

Hopes this helps a little.  i sure others can enlighten you on more and better ways of doing this.

---

### Post by PhantomTurtle on 2012-05-23
> **jmore9 said:**
> If i understand correctly you want to install win7 and then install ubuntu.

First i would get a copy of gparted live , boot from it , and make the partitons that you want for your two os to work in.

For example on my winxp / ubuntu machine i have a 320 gig hard drive (ide) and i have 50 gigs for winxp and the balance for ubuntu.  I started with an empty drive and used gparted live to fromat the drive as follows :

partition 1 - NTFS ( winxp)
partition 2 - EXT4 - (Ubuntu)
partition 3 - Linux Swap

After i get above done i boot with my windows disk and do the windows install on the NTFS partiton.  After windows is all done and installed i boot with the Ubuntu disk and install ubuntu on the EXT4 partiton.  When i install Ubuntu i use the other option and select the ext4 partition as where ubuntu should intall itself to.  I also am lazy so i put everything into / .

After Ubuntu has done its thing at the end it will install grub which i have installed to boot partiton of hda , my only drive so no where else to put it.  Then all done just tweating windows and Ubuntu OS's to where it want them.

Hopes this helps a little.  i sure others can enlighten you on more and better ways of doing this.

There is no need for a gparted live CD because gparted is on the Ubuntu Live CD.

---

