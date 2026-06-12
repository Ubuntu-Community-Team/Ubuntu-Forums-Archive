---
title: "saving Kubuntu 11.10 and software onto blank dvd as bootable file?"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by john7654 on 2012-03-10
[B]Hi guy's,could you help me out here? 
I want to back-up all my downloaded software,in case my P.C goes down,
can anybody help out with a software program that will allow me to present all of the downloaded software as a part of the o.p system (operating system) into the PC...or does anybody have an idea how i can present all of the downloaded software as a one-off executable (saved to disc) :popcorn:
[/B]

---

### Post by sudodus on 2012-03-10
If you want to backup everything on a hard drive, even if it is a multi-boot system with Windows and several linux versions, you can make a clone (exact copy) or image of the drive with ***Clonezilla***. I backup my systems using a live Clonezilla CD drive and make a compressed image of each drive. I write the image to an external hard disk drive via eSATA or USB.

If you have 'only' linux, you need not make a complete image, but can backup your data with ***rsync*** or some GUI tool, for example ***Simple Backup***. But it is still a safe option to use Clonezilla.

---

### Post by mastablasta on 2012-03-10
Mintbackuptool
clonezilla
redobacup


are all backup tools. some will do the whole image of the disk, some (like mint backup tool) can save only porgrammes.

you could also use remastersys to create your own distribution (liveDVD)

---

### Post by oldos2er on 2012-03-10
By default all downloaded packages are stored in /var/cache/apt/archives, unless you've cleaned them out. You can save them to disk and copy them back to that directory, and apt-get will use them.

---

