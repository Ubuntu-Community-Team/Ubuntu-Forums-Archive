---
title: "Can't install Ubuntu Edgy Eft on empty PowerPc ibook G4?"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by jadopadobhimbhadako on 2013-09-15
I downloaded the correct image and burned it onto a DV. When I boot it, a black screen comes up that says boot:
If i press tab, it gives me some options such as live: something.
There's no install option. Then it just boots from the DVD and a lot of  GNOME applets don't work. Everything, including the help window crashes,  so all I can do is turn it off. It doesn't even turn off all the way,  it just ejects the DVD and stops at the shutdown screen. What am I doing  wrong?

---

### Post by Lars Noodén on 2013-09-15
Welcome.

First, support for Edgy Eft ended years ago.  So even if you got it running about the only thing you could do with it would be to upgrade it.  Second, the main version of Ubuntu [no longer supports PPC](http://releases.ubuntu.com/13.04/).  

However, it's not hopeless.  Variations like Lubuntu support the PPC architecture. Go to the Lubuntu download page and scroll down to PowerPC:
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Be sure to read the PowerPC FAQ and Known Issues documents.  You may have to add a line during boot to get the CD/DVD to boot properly, but once you do, it should be smooth sailing.  
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Lubuntu should fit on a CD but you can use a DVD instead if that's what you have.  From there you might be able to install the package "ubuntu-desktop", if it's available for PowerPC, but you'll find that LXDE that comes with Lubuntu is lighter and faster.

---

### Post by sanderj on 2013-09-15
[http://cdimage.ubuntu.com/lubuntu/releases/precise/release/](http://cdimage.ubuntu.com/lubuntu/releases/precise/release/) says

> Mac (PowerPC) and IBM-PPC (POWER5) desktop CD
For Apple Macintosh G3, G4, and G5 computers, including iBooks and PowerBooks as well as IBM OpenPower machines.


So [http://cdimage.ubuntu.com/lubuntu/releases/precise/release/lubuntu-12.04-desktop-powerpc.iso](http://cdimage.ubuntu.com/lubuntu/releases/precise/release/lubuntu-12.04-desktop-powerpc.iso) is probably good for your system

---

