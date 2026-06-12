---
title: "XP laptop network connection problems"
date: 2008-08-27
forum: Other OS Talk
---

### Post by le_vainqueur on 2008-08-27
I have a friend's laptop that I was having difficulty connecting to an encrypted (WPA) wireless network.  The computer is running Windows XP, and was able to connect to wireless networks that are not encrypted, but for those that are, an error message appeared which says something like:

> I don't have it with me now, so I can't get the exact error.  This message appears before ever prompting for the password.  The encrypted network still appears in the "available networks" window, and the strength is very high.  Also, every other computer that I have connected to the encrypted network function properly.  Other encrypted wireless networks present the same issue.  


I just updated all of the drivers and installed service pack 3 in order to get everything up to speed. I am now unable to access the internet even on an unencrypted network.  I get "limitted or no connectivity" even though it does get the network.  When using the diagnose feature in IE7 it says:

> Windows has detected a problem with the Winsock provider catalog on this computer. This catalog allows programs to communicate with this computer accross the network. Would you like Windows to reset the catalog to the default configuration?...

I chose yes, then restarted after its completion.  However, the same problems ensue when it has booted back up, and the diagnose program repeats the same message.


thoughts?

---

### Post by wolfen69 on 2008-08-27
if you have the original cd, insert it, close any windows that open. hit windows key +r and type: sfc /scannow

it will take a little while, but i bet it works.

---

### Post by le_vainqueur on 2008-08-27
I followed the instructions [here]("http://support.microsoft.com/?kbid=811259") to determine if my Winsock was corrupted, but it appears to be fine.  Scratch that off the list...


Ideas?

---

### Post by le_vainqueur on 2008-08-27
> **wolfen69 said:**
> if you have the original cd, insert it, close any windows that open. hit windows key +r and type: sfc /scannow

it will take a little while, but i bet it works.

What will this do?

---

### Post by wolfen69 on 2008-08-27
sfc stands for system file checker. it will repair any corrupted files. i use it alot when i'm out on a job. it will fix alot of problems.

---

### Post by le_vainqueur on 2008-08-27
I don't have the OEM disks since it's not my computer, but I do have a copy of XP Professional (which is installed).  Can I use that?

---

### Post by le_vainqueur on 2008-08-27
> **wolfen69 said:**
> if you have the original cd, insert it, close any windows that open. hit windows key +r and type: sfc /scannow

it will take a little while, but i bet it works.

Okay, I ran this with the disk that I had, but it didn't report anything.  It seemed to run fine (the progress bar steadily filled and reached the end), but there was no result -- good or bad.  What should I see if something was wrong?

---

### Post by le_vainqueur on 2008-08-27
Update: I tried plugging in the wired network to make sure that I had all available updates after SP3, but I receive "limitted or no connectivity" for wired as well.  I also tried disabling the wireless modem entirely to ensure that there was no conflict, but that didn't help

---

