---
title: "Help! Can't Install Any OS!"
date: 2013-05-08
forum: New to Ubuntu
---

### Post by IWantFroyo on 2013-05-08
I bought a new computer recently, and I tried installing Ubuntu. See: [http://askubuntu.com/questions/292148/installation-issue-no-option-to-install](http://askubuntu.com/questions/292148/installation-issue-no-option-to-install)
AskUbuntu couldn't help me with the issue.
Neither Ubuntu 12.04.2 nor 13.04 could get past this issue.

So then I tried installing openSUSE. That didn't work. The installation failed (error code 3030, for anyone curious).

And then I tried restoring Windows 8 from a backup. That failed.


Anyways, what I need is help installing Ubuntu or some Linux distribution.
My hardware is HP h8-1534PC.
[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c03639067&prodSeriesId=5330773](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c03639067&prodSeriesId=5330773)

Post anything that you think might help.

---

### Post by conradin on 2013-05-08
Try disabling the UEFI boot, (secure boot feature) in the BIOS.

---

### Post by fantab on 2013-05-08
Enter your BIOS setup and check the SATA Mode to see what it is set to. We don't want RAID, we like AHCI. 

If it came with Windows8 preinstalled then most likely your HDD will have GPT partition table, did you try to change it msdos? What is the status of "Secure Boot"?

---

### Post by IWantFroyo on 2013-05-08
I tried disabling secure boot.

This time, I didn't get the installer issue, and managed to start installing. It then told me my hard drive was broken and aborted.

I'm going to go back to Best Buy and exchange the computer, considering that's what Windows 8 recovery and openSUSE told me.

Unless, of course, anyone has any suggestions.

---

### Post by fantab on 2013-05-08
> **IWantFroyo said:**
> I'm going to go back to Best Buy and exchange the computer, considering that's what Windows 8 recovery and openSUSE told me.

I guess that's what I'd do, if got the those warnings and errors.

Good Luck...

---

### Post by Archit88 on 2013-05-08
is your HDD partition type is Fixed or Dynamic ? if it is fixed u can not install *nix (any linux distros) .
i was having some what same problem in past , i converted my disk type to dynamic and every thing is okay now.

---

### Post by Lightning Dragon on 2013-05-08
Hi,

I doubt your hard drive is actually broken. I think it is only saying that because of Windows 8 and what previous install it once had on the drive. I would suggest Archit88's suggestion, as I did it once on a hard drive that had Windows 7 and reported being "broken" despite being new. It is worth a shot before you return it, I think. :)

Good luck!

---

### Post by IWantFroyo on 2013-05-08
How do you do that? I haven't seen anything like that in the BIOS.

Edit: Poked around in GParted, but it just gives me errors.

---

### Post by Lightning Dragon on 2013-05-08
Hi,

I am assuming you only want Ubuntu 12.04 LTS, nothing else, on the hard drive so ignore the "without losing any data" in the following link. I'm using a stupid phone for internet right now, so finding the appropriate links may take me a while. I do have this for now though;

[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)

And since you are currently online, I am going to assume you have access to a computer or laptop with USB ports or a disc drive.

---

### Post by IWantFroyo on 2013-05-08
I'm actually typing this from the LiveCD. :/

Edit: I'm downloading and burning now.

---

### Post by Lightning Dragon on 2013-05-08
Hi,

I do believe you can still burn through a LiveCD. I have never actually tried it, but I would suspect it still allows the ability to download and install things. 

The common way this step is done is via Windows, which is what I had to do; reinstall Windows, convert the disk (above links explain how), reboot a few times, turn off, press power button, unplug, plug back in and then power back on into the Ubuntu installation so that I could finally install. I think your _recovery_ of Windows 8 failed because you installed _over_ it, so nothing could be recovered. I would suggest reinstalling Windows 8 and then following this guide;

[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

If "_reinstalling_" is not possible (e.i if you never got a Windows 8 disc for this purpose) then definitely return the computer for a new one and then follow the links given to properly convert to basic disk for installation. :)

---

### Post by Cheesemill on 2013-05-08
> **Archit88 said:**
> is your HDD partition type is Fixed or Dynamic ? if it is fixed u can not install *nix (any linux distros) .
i was having some what same problem in past , i converted my disk type to dynamic and every thing is okay now.

You have this the wrong way round.

If your disk is 'dynamic' then the only OS you can install is Windows as 'dynamic' disks is a proprietary Microsoft technology.
If you want to install any type of Linux then it has to be on a 'fixed' drive as this is the normal setup that adheres to all of the standards.

---

### Post by IWantFroyo on 2013-05-12
I returned the computer and bought a Dell Inspiron notebook instead. :/

Still couldn't get Windows 8 backup to work on it, though, so I decided to just wipe it and build my own computer if that failed. It worked, though.

---

