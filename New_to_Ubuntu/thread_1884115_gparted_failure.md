---
title: "gparted failure?"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by SamUs34 on 2011-11-20
i am trying to have gparted work. and if i am correct i use gparted as a cd to be able to reformat into any new OS i want correct?  please help. and i lost my old thread.

---

### Post by lechien73 on 2011-11-20
Hi,

GParted is a graphical partitioning tool. You can download a LiveCD version from [here.]("http://gparted.sourceforge.net/livecd.php")

Using GParted, you can create, delete, and resize partitions. So, yes - you can reformat partitions ready for a new operating system.

Was that your question?

---

### Post by beew on 2011-11-20
You can use gparted in a Ubuntu live usb or simply install it in any Ubuntu installation (find it in synaptic or the software center).

To use it you want to make sure the drive you want to use gparted on is unmounted. 

The idea is that you need to have gparted installed on somewhere rather than the drive you want to affect.  So if you want to partition your internal drive, you would boot into a Ubuntu live usb and use gparted from there. If you want to partition an external drive, then boot up Ubuntu normally, attach the external drive and use gparted from Ubuntu.

I partition hard drives many time, but never had I use gparted as a standalone live usb or CD. It seems to be wasting a good usb to just put gparted on it while the Ubuntu live iso already includes it.

---

### Post by SamUs34 on 2011-11-20
no it is not working i am using a cd and keeps giving me an error to burn.  wtf.  i would hope the discs aren't ruined but would like to get this to even operate. how else is it possible?  i do not understand this at all.

---

### Post by larrypg on 2011-11-20
Hello,

I am not quite understanding your problem but here goes...gparted is a program.  It can be found on the Ubuntu live cd.  You can run the program if you start up the Ubuntu disk and choose the option to try it.

---

### Post by Mark Phelps on 2011-11-20
> **SamUs34 said:**
> no it is not working i am using a cd and keeps giving me an error to burn.  wtf.  i would hope the discs aren't ruined but would like to get this to even operate. how else is it possible?  i do not understand this at all.
If your question is about the GParted LiveCD ... the file is an ISO file.  You have to use the option to burn an Image file, not to copy files to the CD.

What app are you using to try and burn the file?

What OS are you using to run the app?

---

### Post by waynefoutz on 2011-11-20
is there a Windows install on the disk? If so, launch Windows and run the disk checker in Windows. If gparted detects a Windows partition with disk errors on it, it will abort so as not to break the Windows install.

---

