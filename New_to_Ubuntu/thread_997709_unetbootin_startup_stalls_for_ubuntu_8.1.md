---
title: "unetbootin startup stalls for ubuntu 8.1"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by bluesalt on 2008-11-30
I've followed different instructions to install Ubuntu 8.10 onto my USB stick. I tried pendrivelinux's method of using the script to download the files but to no success for the past 2 days.
Then I tried unetbootin and got everything downloaded into my USB stick. However, I am stuck at the startup.

My notebook (vista OS) starts up immediately with through the USB stick but I get the Unetbootin grey screen telling me that the system will start in 10secs. The message just keeps going on and on. What's happening?

Can I also get this same USB stick to start in Vista as well? Or have a choice in selecting the OS when the notebook boots up? I'm a beginner's beginner in Linux.

Thank you very much for any help.

---

### Post by ugm6hr on 2008-11-30
> **bluesalt said:**
> My notebook (vista OS) starts up immediately with through the USB stick but I get the Unetbootin grey screen telling me that the system will start in 10secs. The message just keeps going on and on. What's happening?

Can I also get this same USB stick to start in Vista as well? Or have a choice in selecting the OS when the notebook boots up? I'm a beginner's beginner in Linux.

I'm afraid you've not really been clear on what happens here.

However, in principle, if you change your BIOS setting (try F2 or F12 at boot-up) to boot from USB as first boot device, it should work.

While you can use a LiveCD within Vista (using Wubi), I don't think the same is possible with a USB install.

PS: Read the edits here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by konge on 2008-12-07
I have the same problem as this guy. When i try to run my ubuntuinstallation installed with unetbootin to a USB-stick i get stuck on the boot sreen. It says "Automatic boot in 10 seconds...", and when i has counted down it starts at 10 seconds again and goes on like this.

I have tried it on two computers, and the same thing happens on both. One running Vista and one already running Ubuntu.

Ofcourse i have set the boot sequence right, if not i would not see the Unetbootin boot screen.

---

### Post by ugm6hr on 2008-12-07
Have you tried the edits to the files on your USB stick here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Also, did you make sure it was FAT32 (i.e. not FAT16) USB format?  I dont fully understand why, but I created a Hardy LiveUSB with unetbootin (and edited file/folder names as link above suggests), and found it worked on 2 of my computers, but reported a "corrupt kernel" on an older computer.  Reformatting to FAT32 and using the same installation appears to have solved that issue.

---

### Post by mgmiller on 2008-12-07
In stead of letting it count down, have you tried hitting "enter"?  That is how I always use unetbootin, and it always starts for me.

---

### Post by bluesalt on 2008-12-08
Thanks for your input everyone. 

1) I've tried installing via unetbootin several times. 
2) Changed BIOS setting. It surely boots up from the USB stick but the unetbootin screen stalls.  I hit 'enter' but nothing changes.
3) My files are FAT32 USB format.  
3) I've done the edits (each time I retried the netbootin method) listed in [https://help.ubuntu.com/community/In...n/FromUSBStick](https://help.ubuntu.com/community/In...n/FromUSBStick). But do these instructions work for 8.10 since I've been reading how easy it is with Ubuntu 8.10

Please help. Thank you

---

### Post by bluesalt on 2008-12-09
Something different happened in my most recent install through unetbootin. The unetbootin screen still stalls but this time it jumped into DOS mode after 10 secs. The message:
Loading /ubnkern
Invalid or corrupt kernal image
Boot:

Then the screen jumps back to unetbootin and when I hit Tab for help, DOS mode again:
ubnkern initrd=/ubninit

What do I do now? I've gone as far as changing the isolinux folder and isolinux.cfg to syslinux.

Thank you

---

### Post by bluesalt on 2008-12-16
My USB stick is a SanDisk Cruzer using U3 Launchpad. Could this be causing problems booting up 8.10?

---

### Post by drinkmocha on 2009-01-11
same thing is happening to me, unetbootin is stuck on '...boot in 10 seconds' then, restarts after counting 10. this is not my first time installing ubuntu, so not sure why this wouldn't work. i am going to redownload the iso and retry and see if it works.

help on this will be appreciated.

---

### Post by drinkmocha on 2009-01-11
SOLVED: I redownloaded the Ubuntu ISO and that fixed the issue.

---

