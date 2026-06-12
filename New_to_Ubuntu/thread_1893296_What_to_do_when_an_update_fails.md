---
title: "What to do when an update fails"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by mortonpj on 2011-12-09
I am a beginner. I run Ubuntu and Kubuntu (oneiric release) installed next to Windows on a variety of machines. I use Windows to back up the entire Ubuntu folder from the C drive to a different location so that I can restore it if the system breaks, which it often does. Most often this happens when I am trying to run an update, and the process gets hung up on one of perhaps more than a hundred separate download/prepare/install operations. The update program suggests running some remedial hocus-pocus from the terminal window, (can't recall the exact magic words, but I am careful to enter them correctly) and this inevitably hangs too. Once this happens you can no longer use the update manager, even after a reboot, and numerous other programs misfire because they were not completely installed. Ultimately I end up going back to windows and restoring an earlier copy of the ubuntu folder, then carefully working around the offending component.

Is this really necessary, or is there some better way to recover from an abortive update?

---

### Post by Bucky Ball on 2011-12-09
In a terminal, one command at a time:

```

sudo apt-get update
sudo apt-get upgrade
```What do you get? Paste the exact error back here so we have a better idea. 'Hocus-pocus' doesn't give any clues on how to help you. ;)

---

### Post by mortonpj on 2011-12-10
The most recent instance after the update manager stalled on the flashplayer downloader, I was instructed to enter the following:

dpkg --configure -a

I prefaced a "sudo"

It ran a few operations and then aborted.

I then restored the ubuntu folder from a backup copy, and updated again, all 191 programs and components, excluding the flashplayer stuff.

Then I saved the folder again and went back to try updating the flashplayer downoader on its own, and it seemed to work all right.

My GRUB screen contains a restore option, which has sometimes worked and sometimes failed in similar situations, but Win 7 seems to seek out and destroy the GRUB configuration - that screen is usually inaccessible after a couple of boots, and I don't know how to get it back. The primary bootup choice: Windows 7 or Kubuntu still works, but contains no restore option.

I will try the commands you suggested the next time they are needed, and carefully record the error message.

---

### Post by Rubi1200 on 2011-12-10
Hi and welcome to the forums mortonpj :)

From your initial description, can we assume you installed using Wubi?

It would be helpful if you could post the results of the boot info script (see link at the bottom of my post).

Thanks.

---

### Post by Viman on 2011-12-10
Hey, your situation sounds a lot like the time in which I had a faulty HDD and nearly gave up on Ubuntu until I found out it was a component's fault. 

Does the upgrade/installation halts in the downloading part or the actual installation of said package?

If everything else fails, I would recommend burning the oneiric ISO to an external medium and performing an installation from there. You can choose to upgrade the OS instead of overwriting the whole disk, so you should be safe.

Hope this helps!

---

### Post by Bucky Ball on 2011-12-10
> **Viman said:**
> 
If everything else fails, I would recommend burning the oneiric ISO to an external medium and performing an installation from there. 



OP already using 11.10. Please read all posts. ;)

10.04 LTS most stable. 11.10 could be the problem ... especially if 11.10 Wubi install.

---

### Post by mortonpj on 2011-12-10
Yes, I am running 11.10 (oneiric), originally installed using wubi. In most respects I like it very much. This was just a periodic update in response to the toaster message "you have ### security updates waiting to be installed." In most respects this is not a serious problem because I can work around it as indicated. It doesn't always happen - many update sessions go smoothly. The specific instance I recounted hung on the install phase after the downloading and preparing had completed.

I'm just curious to know if there is a more elegant way to deal with situations like this, and of course it is interesting that when I mentioned losing GRUB, someone immediately associated that with an wubi install. Learning how to revive GRUB would be another small victory. On machines where the original OS is XP rather than Win 7, GRUB seems to survive just fine, so I attributed this to something designed into Win 7.

---

