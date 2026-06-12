---
title: "USB drives and Open Office (2 questions)"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-04-29
My first question is about USB flash drives.  I am a newly converted windows user, and I don't know where to find the location of a plugged in drive from the terminal.  What directory can I access the files on the drive from in the terminal?  I am used to having a new drive like an H-drive pop up to save to/access files from a flash drive.

My second question is about accessing Open Office from the command line.  Typing "openo" and tab-completing results in "openoffice", but that command doesn't do anything.  As a follow-up to that question, where are all my program files stored?  I've been searching through a bunch of directories and can't find a list of programs that I have installed.

Thanks to anyone who can help.

EDIT: I just found the answer to my second question by browsing through a completely unrelated thread in this forum.  Anyways, I am still puzzled on how to access my USB drive, so if anyone could help me out with that it'd be greatly appreciated.

---

### Post by bobplano on 2008-04-29
Glad you found an answer to the programs question. For the USB, it should be mounted in /media/(nameofdrive). Mine usually has a harddrive icon on the desktop too. If the USB drive isn't there, it might be mounting somewhere else or it might not be mounting at all.

---

### Post by lazyart on 2008-04-29
Yeah, check your desktop.  Or go to Computer and the icon should show up there.

---

### Post by neurostu on 2008-04-29
So ubuntu should automatically MOUNT the usb drive when it is plugged in.  It should mount the drive under the /media directory

Try this:
Plug in your USB drive
Open a terminal
type:
```

cd /media

```
then type:
```

ls

```
this will list everything that is mounted in /media, my USB shows up as PatriotMemory
so if I type
```

cd /media/PatriotMemory

```
I get placed in the root directory of my USB drive
then if you type
```

nautilus .

```
it will open up the Nautilus (the gui file browser) in the root directory of your USB drive.

If your drive isn't showing up under /media try searching the forums or google for "How to mount USB *(with and without your brand of usb)* in ubuntu"

---

### Post by ConMan318 on 2008-04-30
Well I think the problem is that it is not mounting at all.  This is the result of 'ls' in the media directory:

```

xxx@xxx-laptop:/media$ ls
cdrom  cdrom0

```
And going into Places-> Computer shows the CD/DVD drive and 'Filesystem', nothing else.

The USB is from Jaguar, which kind of screws up google searches for how to mount it since Jaguar is an OS for mac.

Anyone know of any way to manually mount it?  I've found a few articles on how to do it, but none have worked since I haven't found one specific to Ubuntu.



Oh, and one other thing, the computer does seem to recognize that it is there:
```

xxx@xxx-laptop:~$ lsusb
Bus 005 Device 006: ID 0420:1307 Chips and Technologies 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c51b Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```
The top one is the port that the flash drive is in (the other is my mouse).  So why doesn't it show up under media?

---

### Post by neurostu on 2008-04-30
Hmm... this might be a bit tricky, try checking out these threads:
[http://www.linuxforums.org/forum/installation/24063-how-mount-usb-drive.html](http://www.linuxforums.org/forum/installation/24063-how-mount-usb-drive.html)
[http://www.mydigitallife.info/2006/09/10/how-to-mount-usb-disk-drive-in-unix-or-linux/](http://www.mydigitallife.info/2006/09/10/how-to-mount-usb-disk-drive-in-unix-or-linux/)
[http://blog.andrewbeacock.com/2007/04/how-to-mount-usb-thumbstick-drive-using.html](http://blog.andrewbeacock.com/2007/04/how-to-mount-usb-thumbstick-drive-using.html)

Granted these might not solve your problem but they probably will provide you with the information and the steps you need to take to solve your problem.

Check out those links and post back if you have any questions.

---

