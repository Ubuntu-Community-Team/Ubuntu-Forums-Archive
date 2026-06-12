---
title: "Virtualbox for Vista and Ubuntu"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by lbarnes on 2008-11-03
hey guys, i've been really intrigued to try out virtualbox
but i'm kinda afraid of messing something up.
i know this has been discussed but i wanna ask you guys myself.
i have vista and intrepid already dual booted.
can i create a virtual box already with these two os's installed?
i would like vista to be the host os.
i'm assuming with virtual box, i can load vista and ubuntu
back and forth without restarting, correct?
and should i install it in vista since i want that to be the host,
or is everything gonna be a clean install after i'm done?
thanks guys

---

### Post by tuxxy on 2008-11-03
If you want the host as Vista then download Virtualbox in Vista and setup a virtual Ubuntu partition, you can see how this is done in the following guide, you may need to scroll down to get to the screenshot guide.

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

This virtual drive will not have an affect on your current installations, it will use free space available in the physical Vista partition.

---

### Post by lbarnes on 2008-11-03
thanks for the quick reply
will the ubuntu i add be the current one with all my settings
or will it be a clean install, basically having two intrepids?
sorry, but i'm scared to death to try this for some reason.
also, i have 8gbs ram, should i just half it?

also, i don't see anything in that guide about a guest os, did i miss that?

---

### Post by lbarnes on 2008-11-03
i'm in the process of doing it now, but it looks like it's gonna install ubuntu all over again
i'm following the directions on the guide you gave me
does this sound right?

---

### Post by zvacet on 2008-11-03
> i'm in the process of doing it now, but it looks like it's gonna install ubuntu all over again

Yes,you will.Just this time you will not install on HDD but on virtual disc.

---

### Post by lbarnes on 2008-11-03
oh, i see, i was hoping i could merge my two installations
as they are now.  thanks

---

### Post by lbarnes on 2008-11-03
well it's saying i can't install it because of the kernel
can i not install 64 bit ubuntu on a 64 bit vista in this vbox?

---

### Post by SunnyRabbiera on 2008-11-03
> **lbarnes said:**
> well it's saying i can't install it because of the kernel
can i not install 64 bit ubuntu on a 64 bit vista in this vbox?

I dont think you can use a 64bit kernel in Vbox, last time I checked

---

### Post by lbarnes on 2008-11-03
oh, i see
let me get this straight...
i make vista the virtual machine name and then under that
under os type, i choose ubuntu.  right?
but, i need to download the 32 bit ubuntu disc?
sorry if i seem slow at this.

---

### Post by Marshal0505 on 2008-11-03
with 2.0.x VirtualBox you can.Make sure to enable the extended features on the advanced tab in 'settings'.This is all assuming you are running on a 64bit host.

---

### Post by SunnyRabbiera on 2008-11-03
> **lbarnes said:**
> oh, i see
let me get this straight...
i make vista the virtual machine name and then under that
under os type, i choose ubuntu.  right?
but, i need to download the 32 bit ubuntu disc?
sorry if i seem slow at this.

I think that is indeed the case.

---

### Post by lbarnes on 2008-11-03
thanks guys

---

### Post by jbg7474 on 2008-11-03
I used virtualbox in hardy (host) to virtualize an existing Vista partition.  There is a way to do this with virtualbox (the one you get from Sun, not the fully open-source version).  I don't remember the precise command, but it is fraught with peril because you basically have to give the whole disk up to virtualbox.  This means that you could accidentally boot the OS that you have already booted!  Yep, that's bad.  I accidentally booted hardy from a virtual machine in hardy with both OS's on the same physical (not virtual) disk.  Fortunately I caught it before damage was done.

There's another kicker with hosting in Linux--Vista will boot but will detect the new virtual hardware as a second installation.  It took about 10-15 times, but eventually the activation algorithm was triggered, and I found myself with an unactivated Vista.  

So, it sounds like you're going about this the right way--hosting in Vista.

---

### Post by lbarnes on 2008-11-03
thanks for all your help guys, but what about the resolution
all it shows is a tiny 800x600 res on my 1900x1200 screen
full screen keeps the tiny size and the only other res size
is even smaller.  is this normal?

---

### Post by tuxxy on 2008-11-05
> **lbarnes said:**
> thanks for all your help guys, but what about the resolution
all it shows is a tiny 800x600 res on my 1900x1200 screen
full screen keeps the tiny size and the only other res size
is even smaller.  is this normal?

Did you install [guest additions?]("http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/")

---

### Post by Ian0426 on 2008-12-14
Once you install guest additions, you should be able to access your full resolution. 

Go up to devices, and mount the CD/DVD ROM and then go down to Install Guest Additions. It will install everything that you need. 

What you can also do, which I think is cool, is adjust the size of the window in the host OS desktop, and the resolution should automatically adjust in the guest OS.

---

### Post by USBuntuInspiron on 2008-12-15
Technically you can't "combine" the two partitions (Vista and Ubuntu) because they run on two different filesystems (NTFS, and EXT3 or EXT2). As for x64 support, yes there is a x64 Virtual Box for download, yes you need a 64 bit host OS, but it will run both x64 and x32 OS's.

---

