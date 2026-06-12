---
title: "Ubuntu 20.04; Should &quot;dpkg -l&quot; list Snap as a program installed?"
date: 2021-02-03
forum: New to Ubuntu
---

### Post by Swan_DB on 2021-02-03
I think I deleted Snap while high on crayons, not 100% sure because, well, I was high on crayons.  I thought I just killed the Snap process; my goal was to reduce the RAM usage Snap process was using, which was a success, HOWEVER: the issue I now have is I can't find "Settings" section and I can't find out how to Suspend after, let's say, 2 hours of inactivity (and I swear I had a Settings section just days before).

I remember reading something about "purge" in regards to removing Snap, but don't remember much more than that.  Should "dpkg -l" list Snap as a program, or how do I go about finding if I have it installed?

Bonus points: Am I missing my Settings section because I did in fact "purge" Snap from my Focal Fossa 20.04 Ubuntu?

edit: I would expect to see "Snap Store" as a program listed, as Snap is not a program, I think.

---

### Post by tea for one on 2021-02-03
Open a terminal and enter:-
```
snap list
```

Further info [https://snapcraft.io/docs/getting-started](https://snapcraft.io/docs/getting-started)

---

### Post by grahammechanical on 2021-02-03
snapd is the

> Background service that manages and maintains installed snaps

[https://snapcraft.io/install/snapd/ubuntu](https://snapcraft.io/install/snapd/ubuntu)

If we remove snapd we will not be able to install and run applications that are in the snap package format. So, the important question is: Is the settings utility a snap application? If it is not and the settings utility is no longer available, then there must be some other cause of the issue.

If you think that you did remove snapd then these are to two commands to re-install snapd

```
sudo apt update
sudo apt install snapd
```

On my Ubuntu 20.04, which has been upgraded from 16.04 through 18.04, I have both a Snap Store which is a snap packaged application and Software which is Gnome Software and is a deb packaged application.

P.S. I have just checked and on my 20.04 the Settings utility is in fact Gnome settings and it is not a snap package utility.

Regards

---

### Post by Swan_DB on 2021-02-03
> **tea for one said:**
> Open a terminal and enter:-
```
snap list
```

Further info [https://snapcraft.io/docs/getting-started](https://snapcraft.io/docs/getting-started)

Shows this: 

Command 'snap' not found, but can be installed with:


sudo apt install snapd

But, I ran ```
dpkg -l
```

and it shows a long list of programs, and 1 of them is snapd, which makes me think maybe I didn't "purge" Snap, but rather did ```
sudo apt-get remove snap
``` ,but that's just a guess.

> **grahammechanical said:**
> 

P.S. I have just checked and on my 20.04 the Settings utility is in fact Gnome settings and it is not a snap package utility.


I think this is the direction I needed.  Not looking to use the Snap Package Manager, just trying to get my Settings application to come back, so I can hopefully add a delay to Suspending/Shutdown.  

Thank you.

I spent, well, I was gonna say an hour, but I guess it was closer to 4 hours searching...  

Best I got so far is my issue might have something to do with either gnome-control-center (haven't looked into this yet).

Or a gnome-settings-daemon (or something like that, not too sure, my brain is fried), which I don't think is where my problem will be, or at least where I'll find it.

Try again tomorrow : )

Preface: might be a big thread as I need lots of help w/ a bunch of different questions, some basic, some not.
Compaq Presario CQ50 - 1 core Pentium 4 CPU, 2 GB RAM.  I looked for answers on my iPhone while out of the house, and found a great answer about BIOS VS UEFI and how to check GRUB2 and do the Boot Loader config file manually if necessary via grub.config (I think), but can't find that thread/post, it was on askubuntu.com; now that I'm back home and looking again on my PC I can't find the thread/post....  :mad:  So.... --->

I get a "boot error" message when loading from the USB w/ the ISO image, make me think the BIOS boot can't handle the ISO file?  I also got a "operating system not found" at some point after that, after doing some stuff I don't exactly remember what, I think I double clicked the ISO file, and it opened up/mounted the Lubuntu files to the same USB stick?  Not sure, but I could see a new mount point /media/username/"some-long-alpha-numeric-name-here", and also /media/username/"Lubuntu-something-here-.ISO", again, it was JUST the iso file until I double clicked the iso file, then it added the second mount (on the same USB stick, I believe) that contained what looked like the files needed to install Lubuntu.  Was this a default Ubuntu 20.04 program that did that, like Unzipped/extraced the files, or something, from the iso file when I doulbe clicked it?

Is it my boot loader that is busted/wrong?  I *think* I have BIOS boot loading, and I *think* I need EFI or maybe UEFI, can someone explain the difference in layman's between these 3?  I *think* BIOS is older and being...  deprecated slowly/replaced by UEFI, is this correct?

I tried Rufus.exe, but it didn't work, it worked before, coming from Windows and installing my first Linux OS, which makes me think Rufus is for Windows, especially with the .exe file?  Maybe I can try a Linux version of Rufus that writes the ISO file to the USB in a format suitable for booting from BIOS or UEFI or EFI?  I don't know, just a guess.

I'd really like to get down into GRUB2 and manually add a "menuentry" into the grub.config file, but I can't find the post/thread that explained how to do that and *why* to do that.  So I can't do it, at least until I find that post again.

I just want to load Lubuntu onto my 4GB USB, then use that USB to "try" or "install" Lubuntu onto my laptop.  I *did* manage to get it to work late last night, but was so tired I couldn't follow the "set up network" instructions and it also failed at "install system and software" stage, possibly because I didn't have the network setup, so it could downloaded needed files?  But I would imagine the needed files *should* be included in the install folders?  Idk...

I just woke up and will likely edit this post in a few hours to simplify/clarify/and get the details correct.  Thanks in advance for any input, it is appreciated.

**Quick Edit:** I'm looking for a "where to start", if anyone can point me in a direction.  Do I look into GRUB2?  Do I look into BIOS vs EFI vs UEFI boot loading?  Do I look into "if my laptop booting process is wrong/broken?

You know what, I just thought about this, I downloaded the "alternative 64-bit" Lubuntu, could that be the issue?  Should I have downloaded the "Desktop 64-bit" Lubuntu from here: [https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

---

### Post by tea for one on 2021-02-04
Are you still looking for Settings?

Applications > Settings

Or via terminal:-```
gnome-control-center 
```

---

### Post by Swan_DB on 2021-02-12
> **tea for one said:**
> Are you still looking for Settings?

Applications > Settings

Or via terminal:-```
gnome-control-center 
```

Just came to mark this [SOLVED!] as that is exactly what it was.  All I had to do was install gnome-control-center via ```
sudo apt install gnome-control-center
```.

Still not sure how I uninstalled it, or maybe it was a bug, idk.  Thanks for the reply though : )

---

