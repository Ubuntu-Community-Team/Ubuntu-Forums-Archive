---
title: "Ubuntu - Windows 7 Dual Boot Problem"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by jrjrjr4 on 2013-01-29
I just installed Ubuntu onto a partition on my PC, which was running  windows 7 and now can no longer boot into windows 7 (says "a disk read  error occurred") or Ubuntu (hangs at startup and mouse/keyboard don't  work). The only OS I can presently run is Ubuntu from a flash drive. 



Any thoughts?

---

### Post by kc1di on 2013-01-29
Hello jrjrjr4 and welcome to ubuntu,

from what you posted it sounds like the grub boot loader got messed up but I'm assuming here.  So let me know a little more about your system.

1. Did you do a Hard drive install of Ubuntu (and What version?)
2. Did you install along side of windows or is this a WUBI install?

That's a start, perhaps we can help better if you answer those questions first.

---

### Post by srekcahrai on 2013-01-29
You hard drive is damaged. You need to replace another hard drive.

---

### Post by furything on 2013-01-29
Before getting hasty with disk failed - nowadays they are smart enabled. Look at the BIOS post boot screen and see if drive says SMART enabled OK or it reports an error.
If reports SMART able disabled then go into BIOS and enable SMART

If it reports an error then yes the drive has failed.

You can boot into live cd and use disk utility which allows you to view the available SMART data and run tests.

If drive reports SMART ok then kc1di looks like he can help you.

---

### Post by Mark Phelps on 2013-01-29
You can get this error if you make the mistake of shrinking the Win7 OS partition from INSIDE the Ubuntu installer.  That has sometimes resulted in filesystem corruption and rendered Win7 unbootable.

So first, you need to answer the questions about HOW you installed Ubuntu.

---

### Post by jrjrjr4 on 2013-01-30
Thanks for your responses. I followed this youtube video ([http://goo.gl/s6oFw](http://goo.gl/s6oFw)) for installing Ubuntu on a separate partition from windows 7.   

I performed the following steps:
1. Opened windows partition management tool and shrunk the partition windows 7 was on by 10 gb. 
2.  Doing this I accidentally converted my  partitions to 'dynamic' and had  to convert them back to 'basic' using a 3rd party program
3.  I booted into Ubuntu using a 4GB flash drive and attempted to install Ubuntu on the  'unallocated space' which was created after shrinking my windows  partition. 


Also, I subsequently ran 'Boot Repair' and got the following URL ([http://paste.ubuntu.com/1587670/](http://paste.ubuntu.com/1587670/)).  I tried rebooting after running Boot Repair and my computer hung on a  command prompt with the message "error: file  '/boot/grub/i386-pc/normal.mod ".

---

### Post by oldfred on 2013-01-30
Boot-Repair reported various errors. Were you not on-line with a wired Ethernet connection when you ran Boot-Repair?

You seem to be missing parts of the system including grub not installed correctly nor all of the kernel boot files.

It also seems a bit strange that HP recovery has efi files, but system is BIOS/MBR. Did you convert from a UEFI install?

---

### Post by jrjrjr4 on 2013-01-30
Hmm, I only have wireless internet available so can't really retry over an Ethernet cable. 

I don't believe I had a UEFI install. I was just running Windows 7 that was installed from my manufacturer.

---

### Post by oldfred on 2013-01-30
The installer usually needs the Ethernet connection to run updates. And it often then cannot install a wireless driver unless you have the wired connection. There just are too many wireless drivers so they do not all fit on the install DVD/Flash drive. 

Does liveCD get you on-line?

But even without updates you should get a full install. Did it report other issues?

---

### Post by jrjrjr4 on 2013-01-30
Yes, I thankfully am able to connect to WiFi when booting off of USB.

I  booted from usb again and ran root repair again, while connected via  wifi and got the message "Linux purge cancelled. Please report this  message to [email]yannubuntu@gmail.com[/email]". Then, I got this URL log  ([http://paste.ubuntu.com/1590468](http://paste.ubuntu.com/1590468)).

After rebooting, got the same blank screen with the same error message as previously.

---

### Post by oldfred on 2013-01-30
It has not changed. 

It might be quicker just to try a full reinstall? But to reuse same partitions you have to use manual install or Something else and chose existing partition for / (root) and format ext4. You have a separate /home so you can reuse it by choosing it but NOT format, swap should automatically be chosen.

Did you install a 64 bit version? If not I would.

---

### Post by furything on 2013-02-01
If you are reinstalling the same version of ubuntu to the same directory structure you need to delete either all folders and files from the system (\root) or just leave behind your home directory.

I have found the reinstall does not correct configuration files so you can end up in the same boat. You must clean the partition first.

I recommended the same here
[http://ubuntuforums.org/showthread.php?t=2107354&page=5](http://ubuntuforums.org/showthread.php?t=2107354&page=5)
as they found the same issue as I have had. Deleting the folder structure also worked for them.

---

