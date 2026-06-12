---
title: "how to uninstall ubuntu"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by iantarantin on 2012-11-28
Hello i am new,  my recent vmware xpired so i tried installing ubuntu from my live cd, anyways i installed it twice(when computer boots up there are multiple ubuntu) how do i uninstall without getting rid of my other OS's? the live cd has no option of removing ubuntu

---

### Post by HermanAB on 2012-11-28
Hmmm, this is the kind of question that is probably best left unanswered.  

If you are a new user with so little knowledge that you have to ask how, then chances are that you will totally FUBAR your machine while trying to remove stuff.

---

### Post by dannyboy79 on 2012-11-28
you would need to show us the output from a few commands.
```
sudo fdisk -l
```

that will show us your hard drives and partition tables. Also, from the version of Ubuntu you want to KEEP, issue this

```
mount
```

and tell us the output of that as well.

---

### Post by audiomick on 2012-11-28
It is fairly easy, actually. What you need to do in principle is 
Delete the partition that the install that you want to remove is on.
Resize the other partitions to take over the space, or just leave it empty for future use.
Run update-grub if grub is your primary bootloader, or update whatever bootloader it is that you are using.

It would help to give more precise advice if we knew exactly what is installed on the computer. Your post indicates that there are several OSs on there. 

I would suggest following the instructions here
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
to get the boot repair tool.

Actually, I just noticed something new. On there, there is a link to here (in the "on CD section" )
[https://help.ubuntu.com/community/UbuntuSecureRemix]("https://help.ubuntu.com/community/UbuntuSecureRemix")
That claims to have a tool on it for removing OSs from your computer. You might like to try that.

If you don't want to attempt that on your own, you could do what I was going to suggest. Use the boot repair tool to run the boot info script. You do not, at this stage, want to run boot repair to repair anything. The idea is just to run the boot info script to get a rather extensive list of info about the state of your install. Using this, people who might be able to give you instructions can do so more precisely.

---

### Post by QIII on 2012-11-28
Before we get too far afield here...

Are you sure there are multiple installs, or is GRUB showing you one install with a couple of kernel versions?

What version of Ubuntu are you using?  If earlier than 12.10, you'll likely see the originally installed kernel and perhaps another, updated kernel.

If 12.10, you'll see something like "Other Ubuntu options".

---

### Post by audiomick on 2012-11-28
> **QIII said:**
> Are you sure there are multiple installs, or is GRUB showing you one install with a couple of kernel versions?

A relevant question. If the OP is unsure, then I would once again recommend obtaining the output from the boot info script. 


Incidentally, I think 11.10 already had the "other options" entry in the grub menu. I have that on my desktop, but can't check for sure as the machine is in the shop at the moment.

---

### Post by QIII on 2012-11-28
GRUB 2.0 is subtly different.  Maybe that's not exactly it.

---

### Post by YannBuntu on 2012-11-29
Hello

As advised above, it is safer that we see the exact content of your disks via a BootInfo.
Please first:
1) burn a Ubuntu-Secure-Remix liveCD or liveUSB (because it contains Boot-Repair and OS-Uninstaller that you will need in the next steps)
2) boot your pc on this disk, choose "Try Ubuntu", click on the "Boot-Repair" icon which is on the left-side of the screen. This will launch Boot-Repair. In the Boot-Repair main window, please click the "Create BootInfo summary" button (NOT the "Recommended Repair" button). This will gather information, and display an URL (something like **paste.ubuntu.com/1234567** ). Please write this URL on a paper and indicate it to us.

Remark: details of the procedure are here: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

