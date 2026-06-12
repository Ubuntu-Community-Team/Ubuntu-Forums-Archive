---
title: "Tomboy 0.3.2 on Ubuntu Hoary"
date: 2005-05-20
forum: Outdated Tutorials &amp; Tips
---

### Post by sebgate20 on 2005-05-20
It's another tutorial from Evolution Colt!

Tomboy 0.3.1 is included with Ubuntu Hoary but this has a nasty bug which means that you can't open a note from Beagle or using the tomboy --open-note command. However, this is fixed in Tomboy 0.3.2 so this tutorial explains how to install Tomboy 0.3.2 on Hoary.

PLEASE NOTE: This is a package from Breezy Badger. We (Evolution Colt) use Tomboy 0.3.2 and find it to be very stable (even more stable than 0.3.1) but remember this is testing software so be careful!

You should also have Mono 1.1.7 installed from Backports. You find information on this in the Beagle tutorial but I am writing a seperate one just for Mono 1.1.7

You can find the tutorial here at: [http://www.evolutioncolt.com/mainweb/?q=node/13](http://www.evolutioncolt.com/mainweb/?q=node/13)

As usual, leave some feedback!

Seb

---

### Post by Heliode on 2005-05-20
Thanks a lot, I've been looking for a way to make my note-taking more efficient, and this seems like just what I need!

---

### Post by Ainvar on 2005-05-23
Has anyone gotten this to work?

---

### Post by harryc on 2005-05-23
I have it working here on Hoary 5.04, Mono 1.1.7. The Tomboy crash on Beagle/Best note selection bug is indeed fixed.

---

### Post by ChamPro on 2005-06-07
Awww. The Ubuntu Archive no longer contains the 0.3.2 deb. Is there an alternative place we could download it?

---

### Post by Majlo on 2005-06-07
[QUOTE=ChamPro]Awww. The Ubuntu Archive no longer contains the 0.3.2 deb. Is there an alternative place we could download it?[/QUOTE]

Try this 
[http://getsweaaa.com/~tseng/ubuntu-mono/binary/](http://getsweaaa.com/~tseng/ubuntu-mono/binary/)

---

### Post by ametade on 2005-06-07
You can still find it at Breezy archives:

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Ft%2Ftomboy%2Ftomboy_0.3.2-4ubuntu5_i386.deb&md5sum=fe6cc42b58e72c369ab117bfa6c15884&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Ft%2Ftomboy%2Ftomboy_0.3.2-4ubuntu5_i386.deb&md5sum=fe6cc42b58e72c369ab117bfa6c15884&arch=i386&type=main)

---

### Post by ChamPro on 2005-06-07
Tomboy 0.3.2 installed fine. But it doesn't run without dbus errors. It just keeps making more and more requests for upgrading the dbus packages. I'm not sure how stable this is really going to make my system if Tomboy works better but other things crash because of these dbus updates.

---

### Post by ChamPro on 2005-06-14
With some of the latest Backports updates, those dbus upgrades are not needed.

However, they got rid of the Tomboy icon... I liked that icon. Now it's a generic one that doesn't look good at 24x24. Boo.

---

### Post by nuggien on 2005-06-30
[QUOTE=ChamPro]Tomboy 0.3.2 installed fine. But it doesn't run without dbus errors. It just keeps making more and more requests for upgrading the dbus packages. I'm not sure how stable this is really going to make my system if Tomboy works better but other things crash because of these dbus updates.[/QUOTE]

[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Ft%2Ftomboy%2Ftomboy_0.3.2-8_i386.deb&md5sum=cfa4322faacac371c017aeb88da8f98a&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Ft%2Ftomboy%2Ftomboy_0.3.2-8_i386.deb&md5sum=cfa4322faacac371c017aeb88da8f98a&arch=i386&type=main)

tomboy 0.3.2-8 worked okay for me w/o dbus errors.

---

### Post by jadugarr on 2005-07-16
I tried using the version from breezy that was posted as well as trying the latest version from breezy.  Both crashed when trying to be loaded and gave this error.  

```
The panel encountered a problem while loading "OAFIID:TomboyApplet".
``` 

Perhaps compiling from source will give me better results?

---

### Post by rwabel on 2005-07-27
[QUOTE=jadugarr]I tried using the version from breezy that was posted as well as trying the latest version from breezy.  Both crashed when trying to be loaded and gave this error.  

```
The panel encountered a problem while loading "OAFIID:TomboyApplet".
``` 

Perhaps compiling from source will give me better results?[/QUOTE]
 same for me with the backport version from hoary. I started it from console with --tray-icon and got the following error message:
** (Tomboy:20315): WARNING **: The class DBus.Service could not be loaded, used in /usr/lib/tomboy/Tomboy.exe (token 0x0100000c)

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in <0x00045> Tomboy.TomboyTrayIcon:.ctor (Tomboy.NoteManager manager)
in <0x00022> Tomboy.TomboyTrayIcon:.ctor ()
in <0x00019> Tomboy.Tomboy:StartTrayIcon ()
in <0x000d8> Tomboy.Tomboy:Main (System.String[] args)

---

### Post by rwabel on 2005-07-27
[QUOTE=rwabel]same for me with the backport version from hoary. I started it from console with --tray-icon and got the following error message:
** (Tomboy:20315): WARNING **: The class DBus.Service could not be loaded, used in /usr/lib/tomboy/Tomboy.exe (token 0x0100000c)

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in <0x00045> Tomboy.TomboyTrayIcon:.ctor (Tomboy.NoteManager manager)
in <0x00022> Tomboy.TomboyTrayIcon:.ctor ()
in <0x00019> Tomboy.Tomboy:StartTrayIcon ()
in <0x000d8> Tomboy.Tomboy:Main (System.String[] args)[/QUOTE]
 I've reinstalled libdbus-cil and now it's working, maybe it helps you too

---

