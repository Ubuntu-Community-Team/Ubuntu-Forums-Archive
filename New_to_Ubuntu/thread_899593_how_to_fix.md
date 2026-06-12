---
title: "how to fix"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by sheroxe on 2008-08-24
Hi, i am trying to install ubunt but i can't make a new partition cause it says it has an error. 

I ran the live cd of ubuntu and opened the gparted program, when it scans it detects my partition where windows it's installed but it shows a warning sign (an exclamation mark with a yellow triangle) saying the disk has an error "NTFS is inconsistent, run chkdsk /f on windows then reboot it TWICE"

I tried checking the disk with gparted but it says 'an error ocurred' and it doesnt check it.

In windows i have tried chkdsk /f, chkdsk /r, and chkdsk from the drive properties, they all have to be programmed to run after reboot but when when chkdsk starts it freezes at 2%, i let the laptop on the whole night and it's still at 2%.

Any idea how can i fix this disk error?

---

### Post by halitech on 2008-08-24
try doing a defrag from within windows a few times and see if it will let you do a chkdsk after that

---

### Post by sheroxe on 2008-08-24
i already defrag like 3 times :S

---

### Post by halitech on 2008-08-24
can you boot into safe mode and run it? maybe your swap file is corrupted and causing the problem (I'm guessing here, been awhile since I've done much under windows)

---

### Post by sheroxe on 2008-08-24
The problem is not running it, it runes. I think there's no need for safe mode cause it runes before opening. The thing is that it never finishes, it stays frozen at 2%

---

### Post by alienexplorers on 2008-08-24
Are you trying to run this on the windows partition or on a seperate disk?

---

### Post by halitech on 2008-08-24
> **sheroxe said:**
> The problem is not running it, it runes. I think there's no need for safe mode cause it runes before opening. The thing is that it never finishes, it stays frozen at 2%

if there is an issue with a file being in use it will start to run but hang on whatever the file is that is in use. Worth a shot.

---

### Post by sheroxe on 2008-08-24
> **halitech said:**
> if there is an issue with a file being in use it will start to run but hang on whatever the file is that is in use. Worth a shot.

what do u mean

---

### Post by halitech on 2008-08-24
when windows is running, there are files that are in use. If there is an issue with a file that is in use, chkdsk will start but could hang on checking that file

---

### Post by michael1234 on 2008-08-24
Try running chkdsk from outside the hard disk.

[Go here]("http://www.bootdisk.com/bootdisk.htm") and download a boot disk maker, then reboot and run chkdsk from this disk. Perhaps your native version of chkdsk is wonky.

--M

---

### Post by alzie on 2008-08-24
You can try running chkdsk /r from the recovery console.

In any case I'd backup any important files just in case.  chkdsk should not be having this kind of an issue.

---

### Post by sheroxe on 2008-08-24
> **alzie said:**
> You can try running chkdsk /r from the recovery console.

In any case I'd backup any important files just in case.  chkdsk should not be having this kind of an issue.

how do i do that?

---

### Post by cjm5229 on 2008-08-24
If you are new to Ubuntu and just want to try it out, Install it in Windows using Wubi. You won't have to Partition your HDD and can remove it later if you wish by simply uninstalling it with Windows Remove Programs.. Put The CD in the drive with Windows running and you should get a window popping up that asks if you want to install it in Windows. just go ahead and install it. If you decide later that you want a permanent install you can study Partitioning here [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
before you start. There are some very good How to's there.

---

### Post by alzie on 2008-08-25
I snipped this from MicroSoft's site : [http://support.microsoft.com/kb/307654/en-us#3](http://support.microsoft.com/kb/307654/en-us#3)


> To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.	Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.	When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.	If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.	When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.	At the command prompt, type the appropriate commands to diagnose and repair your Windows XP installation.

For a list of commands that are available in Recovery Console, type recovery console commands or help at the command prompt, and then press ENTER.

For information about a specific command, type help commandname at the command prompt, and then press ENTER.
6.	To exit the Recovery Console and restart the computer, type exit at the command prompt, and then press ENTER.

I agree that Wubi is a good alternative to try things out.  That is how I started.

I hope this helps

---

### Post by sheroxe on 2008-08-25
That wont work, i have windows vista and there's no recovery console

but my problem is fixed now, i downloaded vista service pack 1 and ran chkdsk after that and it worked fine.

thanks anyway :)

---

