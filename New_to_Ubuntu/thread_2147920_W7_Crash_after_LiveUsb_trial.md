---
title: "W7 Crash after LiveUsb trial"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by CheddarMogul on 2013-05-23
Hi there, I made a LiveUsb for Ubuntu 13.04 to check it out on trial mode, it booted rather slowly and it would freeze for a few seconds every time i tried to check something, like checking the volume, about a minute after logging in, I tried to change the mouse sensitivity, Ubuntu froze in this screen for 5 minutes so I decided to reboot.  I had the iso for the previous more stable Ubuntu version so I decided to go to Windows 7 64 again to make another liveusb with that one, but Windows BSODs every time after the windows black screen.  I thought harming the main Win installation was not possible using a livecd-usb so I'm at a loss as to what really happened , couldn't find anything googling so here I am.  Any help is welcomed, Thanks!

---

### Post by grahammechanical on 2013-05-23
Please explain what you mean by this statement

> about a minute after logging in,

I am typing this from a 13.04 live session. I am using it to resize and move some parttions and I got bored waiting for the operations to complete. So, I came on to Ubuntu forums. I have never needed to log in to a ubuntu live session. Please explain more clearly because right now I am thinking that you installed Ubuntu.

Regards.

---

### Post by CheddarMogul on 2013-05-23
I mispoke, no login was necessary, I meant to say one minute after being in the main desktop.  I am 100% sure that Ubuntu is not installed in any way, I can still start the the live-usb and use the trial option without any trouble besides the random freezing that occurs now and then when I do something, like opening new tabs in Firefox.

---

### Post by Mark Phelps on 2013-05-23
> **CheddarMogul said:**
> ... I thought harming the main Win installation was not possible using a livecd-usb ...

When you run using the LiveCD or LiveUSB mode, Ubuntu creates a RAMDisk (maps a section of system memory to behave like a filesystem) and it uses that.  Which is one of the reasons it is so slow -- it has to retrieve everything it needs from the CD/USB and write it to the RAMDisk before it can use it.

However, that said, it is also possible to mount existing hard drive partitions while running in LiveCD or LiveUSB mode, and if that is done, then changes can and will be made to the filesystems on the hard drive.

So, while it is "possible" to harm the main Win installation, that does not happen unless you write to one or more of the Windows partitions.

---

### Post by CheddarMogul on 2013-05-23
One of the things I did in that one minute before Ubuntu crashed, was to check on the folders in the hdds that I use on W7, I only looked at them to see if it was possible to see them at all and was surprised to find them there.  Could it be that my "looking" at C is the cause of this?  Thanks!

---

### Post by leunam12 on 2013-05-23
Can you run windoze in safe mode and do a system restore to a point before you tried the live-usb?

---

### Post by CheddarMogul on 2013-05-23
> **leunam12 said:**
> Can you run windoze in safe mode and do a system restore to a point before you tried the live-usb?  No, for some reason it seems at some point in the far past, I deactivated System Restore, so I have no point to go back to. Very stupid, but I really cant remember why on earth i did it, so yeah...

---

