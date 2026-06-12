---
title: "Aptitude wants to update 29 Kernel Parts? 3 gig of updates?"
date: 2013-02-13
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-02-13
Is this sensible?

```
mark@Lexington-19:~$ sudo aptitude install -f
The following NEW packages will be installed:
  libftdi1 linux-headers-3.2.0-24 linux-headers-3.2.0-24-generic 
  linux-headers-3.2.0-24-generic-pae linux-headers-3.2.0-25 
  linux-headers-3.2.0-25-generic linux-headers-3.2.0-25-generic-pae 
  linux-headers-3.2.0-26 linux-headers-3.2.0-26-generic 
  linux-headers-3.2.0-26-generic-pae linux-headers-3.2.0-27 
  linux-headers-3.2.0-27-generic linux-headers-3.2.0-27-generic-pae 
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic 
  linux-headers-3.2.0-29-generic-pae linux-headers-3.2.0-30 
  linux-headers-3.2.0-30-generic linux-headers-3.2.0-30-generic-pae 
  linux-headers-3.2.0-31 linux-headers-3.2.0-31-generic 
  linux-headers-3.2.0-31-generic-pae linux-headers-3.2.0-32 
  linux-headers-3.2.0-32-generic linux-headers-3.2.0-32-generic-pae 
  linux-headers-3.2.0-33 linux-headers-3.2.0-33-generic 
  linux-headers-3.2.0-33-generic-pae linux-headers-3.2.0-34 
  linux-headers-3.2.0-34-generic linux-headers-3.2.0-34-generic-pae 
  linux-headers-3.2.0-35 linux-headers-3.2.0-35-generic 
  linux-headers-3.2.0-35-generic-pae linux-headers-3.2.0-36 
  linux-headers-3.2.0-36-generic linux-headers-3.2.0-36-generic-pae 
  linux-image-3.2.0-25-generic linux-image-3.2.0-25-generic-pae 
  linux-image-3.2.0-26-generic linux-image-3.2.0-26-generic-pae 
  linux-image-3.2.0-27-generic linux-image-3.2.0-27-generic-pae 
  linux-image-3.2.0-29-generic linux-image-3.2.0-29-generic-pae 
  linux-image-3.2.0-30-generic linux-image-3.2.0-30-generic-pae 
  linux-image-3.2.0-31-generic linux-image-3.2.0-31-generic-pae 
  linux-image-3.2.0-32-generic linux-image-3.2.0-32-generic-pae 
  linux-image-3.2.0-33-generic linux-image-3.2.0-33-generic-pae 
  linux-image-3.2.0-34-generic linux-image-3.2.0-34-generic-pae 
  linux-image-3.2.0-35-generic linux-image-3.2.0-35-generic-pae 
  linux-image-3.2.0-36-generic linux-image-3.2.0-36-generic-pae lirc 
  setserial 
The following packages will be REMOVED:
  libboost-program-options1.46.1{u} 
0 packages upgraded, 61 newly installed, 1 to remove and 0 not upgraded.
Need to get 1,001 MB/1,001 MB of archives. After unpacking 3,429 MB will be used.
Do you want to continue? [Y/n/?] Y
```


I've been trying for 3 weeks to remove the old outdate kernel parts. Anybody got a clue what is the safe way to fix this?

---

### Post by Bucky Ball on 2013-02-13
Grub Customizer is your friend. Else go to Software Centre and search for the kernel numbers you want gone and uninstall.

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

Not sure why you're using that command. All you really want is these two:

```
sudo apt-get update
sudo apt-get upgrade
```

This will only upgrade apps and anything you have installed, not the OS release to the next one. Keep running them until there is nothing left. Looks like you haven't updated in some time ...

Set it for once a week and just install updates when you are notified of them.

---

### Post by CharlesA on 2013-02-13
Why are you running aptitude with -f?

>  -f
           Try hard to fix the dependencies of broken packages, even if it
           means ignoring the actions requested on the command line.

           This corresponds to the configuration item
           Aptitude::CmdLine::Fix-Broken.


[http://manpages.ubuntu.com/manpages/lucid/man8/aptitude.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/aptitude.8.html)

---

### Post by DuckHook on 2013-02-13
I don't use aptitude much, but the first thing I would consider is: how are you removing the old kernels? Are you bypassing the whole dpkg system by deleting them directly? If so, the dpkg database (of which aptitude/apt/synaptic are just high-level manipulation apps) will not have registered your intent to delete, will just note that they are missing, and will reinstall them again. My understanding is that old kernels should be deleted using aptitude/apt/synaptic. Thereafter, dpkg will be keyed to knowing that you've intended to delete them and will not bring them back in at the next update. If this is already how you are deleting them, then I'm stumped.

<edit>
Smarter gurus have spoken whom you should listen to over me.
</edit>

---

### Post by Mark_in_Hollywood on 2013-02-13
> **CharlesA said:**
> Why are you running aptitude with -f?

[http://manpages.ubuntu.com/manpages/lucid/man8/aptitude.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/aptitude.8.html)

I had hoped to avoid bringing this into the post. My Blackberry (smart?phone) is no longer placing (registering) onto my Xubuntu desktop when plugged into it's usb cable.

lsusb says:

Bus 001 Device 029: ID 0fca:0004 Research In Motion, Ltd. **Blackberry Handheld**

so it's somewhere.

I see boot-time messages about something to do with blackberry, but, at boot-time, messages scroll like lighting off the screen. I used aptitude -f hoping to fix the problem. What I found is something else. That aptitude wants a gig of downloads to update out-of-date stuff is somewhat scary and I want to avoid d/l-ing a gig anyway. But if you think that 'safe' I'm OK with it.

I pasted one of the lines from the terminal into Ub's Software Center, thinking I could then delete it, but ooopppssss! There it is. Or isn't. It's not installed according to the Center.

Please see screenshot.

---

### Post by Mark_in_Hollywood on 2013-02-13
> **DuckHook said:**
> I don't use aptitude much, but the first thing I would consider is: how are you removing the old kernels? Are you bypassing the whole dpkg system by deleting them directly? If so, the dpkg database (of which aptitude/apt/synaptic are just high-level manipulation apps) will not have registered your intent to delete, will just note that they are missing, and will reinstall them again. My understanding is that old kernels should be deleted using aptitude/apt/synaptic. Thereafter, dpkg will be keyed to knowing that you've intended to delete them and will not bring them back in at the next update. If this is already how you are deleting them, then I'm stumped.

<edit>
Smarter gurus have spoken whom you should listen to over me.
</edit>

Here is a screenshot of what aptitude thinks needs updating and Synaptic Pkg Mgr thinks is not installed.

---

### Post by CharlesA on 2013-02-13
> **Mark_in_Hollywood said:**
> I see boot-time messages about something to do with blackberry, but, at boot-time, messages scroll like lighting off the screen. I used aptitude -f hoping to fix the problem. What I found is something else. That aptitude wants a gig of downloads to update out-of-date stuff is somewhat scary and I want to avoid d/l-ing a gig anyway. But if you think that 'safe' I'm OK with it.

I pasted one of the lines from the terminal into Ub's Software Center, thinking I could then delete it, but ooopppssss! There it is. Or isn't. It's not installed according to the Center.

Please see screenshot.

Huh? If you want to check what messages appear during boot, check /var/log/boot.log

As far as the kernel problem, run this and post the results please:

```
dpkg -l | grep kernel
```

---

### Post by Mark_in_Hollywood on 2013-02-13
```
mark@Lexington-19:~$ dpkg -l | grep kernel
ii  kerneloops-daemon                      0.12+git20090217-1ubuntu19                          kernel oops tracker
ii  libdrm-intel1                          2.4.39-0ubuntu0.1                                   Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-nouveau1a                       2.4.39-0ubuntu0.1                                   Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-radeon1                         2.4.39-0ubuntu0.1                                   Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm2                                2.4.39-0ubuntu0.1                                   Userspace interface to kernel DRM services -- runtime
ii  linux-firmware                         1.79.1                                              Firmware for Linux kernel drivers
ii  linux-firmware-nonfree                 1.11ubuntu1                                         Non-free firmware for Linux kernel drivers
ii  linux-generic                          3.2.0.37.45                                         Complete Generic Linux kernel
ii  linux-headers-3.2.0-37                 3.2.0-37.58                                         Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-37-generic         3.2.0-37.58                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-37-generic-pae     3.2.0-37.58                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-generic                  3.2.0.37.45                                         Generic Linux kernel headers
ii  linux-headers-generic-pae              3.2.0.37.45                                         Generic Linux kernel headers
ii  linux-image-3.2.0-37-generic           3.2.0-37.58                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-37-generic-pae       3.2.0-37.58                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.2.0.37.45                                         Generic Linux kernel image
ii  linux-image-generic-pae                3.2.0.37.45                                         Generic Linux kernel image
ii  module-init-tools                      3.16-1ubuntu2                                       tools for managing Linux kernel modules
ii  nvidia-current                         295.40-0ubuntu1.2                                   NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  rsyslog                                5.8.6-1ubuntu8                                      reliable system and kernel logging daemon
ii  udev                                   175-0ubuntu9.2                                      rule-based device node and kernel event manager
```

---

### Post by Bucky Ball on 2013-02-13
Normal. You haven't updated for some time. Have you upgraded from one release to another lately?

---

### Post by Mark_in_Hollywood on 2013-02-13
This is what happened:


[http://ubuntuforums.org/showthread.php?t=2109070](http://ubuntuforums.org/showthread.php?t=2109070)


It's lengthy. I could not boot. I could not Grub-Recover. I believe that the 3.2.0-37-generic-pae  was eventually re-installed and the OS could boot and operate normally.

The video card had to be replaced. The on-board video was used while that card was changed. That lost the Grub Recovery screen. I didn't know that old kernels, images, pae-s, should be removed. Many other problems exerted themselves at this time. I was hoping to not bring this up, too.

---

### Post by CharlesA on 2013-02-13
What happens if you just run this:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Mark_in_Hollywood on 2013-02-13
Usual lengthy list of repo lines, followed by:


Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


full terminal output at:

[http://pastebin.com/sJXiBzvQ](http://pastebin.com/sJXiBzvQ)

---

### Post by DuckHook on 2013-02-13
> **Mark_in_Hollywood said:**
> This is what happened:


[http://ubuntuforums.org/showthread.php?t=2109070](http://ubuntuforums.org/showthread.php?t=2109070)


It's lengthy. I could not boot. I could not Grub-Recover. I believe that the 3.2.0-37-generic-pae  was eventually re-installed and the OS could boot and operate normally.

The video card had to be replaced. The on-board video was used while that card was changed. That lost the Grub Recovery screen. I didn't know that old kernels, images, pae-s, should be removed. Many other problems exerted themselves at this time. I was hoping to not bring this up, too.

...Lordy, Lordy. Ooohh my. Okay, let's take a deep breath here.

1. Firstly, don't go executing any commands until you are confident that you understand what the command is going to do.

2. Listen to *@Bucky Ball* and *@CharlesA* (i.e. gurus) before you go listening to guys like me--even with respect to what follows.

3. It's time to see a bigger picture of what you are trying to do.
   a. Is this a production machine? In other words, does it positively have to be rock stable or can you tinker with it?
   b. Given all that you've been through and hopefully learned, describe your backup routine.
   c. Are you prepared to re-install if needed?
   d. Is your objective to work or to learn? And if a combo of both, weighted towards which?

You can probably sense where I'm going with this... the time that you've committed to solving your various issues these past weeks could very well have equalled re-installing five times over. Of course, there's not a better way to learn than wrestling with a cussed installation, but my problem, at least, is that I have no idea what the state of your OS is by now, and I doubt it can be brought back to a reference state. A highly irregular state is okay for a hacker, but my experience has been that irregular states are just poison for general users and will continue to give you problem after problem, with each jerry-rig, fix or workaround only increasing irregularity and instability.

So, it's obviously your call, but my recommendation is to reinstall your OS at this point. You would then have a reference install and solve not only this problem, but forestall future problems as well.

---

### Post by Mark_in_Hollywood on 2013-02-13
I'm going to try to simplify this as best I can. This is a production machine. There is no other OS to use. Although I do have a LiveUSB if necessary. Deja-Dup runs bi-monthly backups and I have done a BU more recently as this problem has made me understandably nervous.

To reiterate: the problem is that the Blackberry no longer put's it's icon on the Desktop. If I could access without an icon any longer, I wouldn't care. Not being able to access the 2-gig card in it is not much fun, but again, I have an external reader and can move files on and off it.

I know of no app or software program not functioning at this time and cannot see a reason sufficient to re-install the OS. At least, not until something breaks. As for working/learning, well, again, this 'puter is doing OK at this time. Taken as a whole. It prints, the internet is fine, MythTV runs (well that the once exception to the paragraph below). As for "stability" - I'm not a Unix/Linux tech. I can put and paste to the terminal. Maybe do nano, too, if it's easier. But do I want to mess with the innards in an "experimental" way. No. If other haven't had this problem, and it requires multiple people around the globe to solve this, if I mess it up I won't do it. T'aint fair to others who have problems and need help. 

In all these woes however, *cheers* to Linus Torvalds and the Linux Community for building the world's most robust operating system and ancillary software.

---

### Post by CharlesA on 2013-02-14
OK, so you don't have anything that needs to be updated/upgraded.

Does the blackberry show up if you do:

```
sudo fdisk -l
```

If it still isn't showing up, you could run this to "attempt to fix broken dependencies" but I don't know if it's really needed or not...

```
sudo apt-get install -f
```

It will probably have to download a gig of files in order to repair whatever it thinks is broken.

---

### Post by Mark_in_Hollywood on 2013-02-14
> **CharlesA said:**
> OK, so you don't have anything that needs to be updated/upgraded.

Does the blackberry show up if you do:

```
sudo fdisk -l
```

If it still isn't showing up, you could run this to "attempt to fix broken dependencies" but I don't know if it's really needed or not...

```
sudo apt-get install -f
```

It will probably have to download a gig of files in order to repair whatever it thinks is broken.

sudo fdisk -l 

does NOT show the device or filesystem.

I'm not certain I want a gig of downloads. Eventually, I will upgrade to Quantal or beyond. If this had been a fairly straighforward problem/solution I would jump at it, but as it as, it's not worth jeopardizing an OS that has worked flawlessly since Maverick.

Thank you for your time and trouble.

---

### Post by CharlesA on 2013-02-14
I doubt downloading the ton of kernels in the OP would fix the problem, or affect the OS in a negative light, but if you want to leave it as-is, feel free. :)

If you want to work on the blackberry problem, you might want to see what dmesg says after you plug it in.

```
dmesg | tail
```

---

### Post by mc4man on 2013-02-14
You have the latest 2 kernels for 12.04 excluding precise-proposed.
If you thought the kernel was responsible for the blackberry issues & wished to test some older ones that are available you could certainly do so.
I'd try one at a time, - install the needed packages, (if possible), typically 3 per kernel. Then add to grub, (sudo update-grub) & restart to that kernel to see.

Because you are using nvidia drivers you'd want to make sure a kernel module is built for each testing kernel, easier for these purposes to remove the nvidia packages & use nouveau for this testing. 
(assuming your card works half-decently with nouveau

Also to consider - 
there is an updated 3.2 kernel in precise-proposed & also a 3.5 version (quantal-lts

---

### Post by Mark_in_Hollywood on 2013-02-14
Just to see what might happen:


mark@Lexington-19:~$ sudo aptitude install -f
The following NEW packages will be installed:
  libftdi1 linux-headers-3.2.0-24 linux-headers-3.2.0-24-generic 
  linux-headers-3.2.0-24-generic-pae linux-headers-3.2.0-25 
  linux-headers-3.2.0-25-generic linux-headers-3.2.0-25-generic-pae 
  linux-headers-3.2.0-26 linux-headers-3.2.0-26-generic 
  linux-headers-3.2.0-26-generic-pae linux-headers-3.2.0-27 
  linux-headers-3.2.0-27-generic linux-headers-3.2.0-27-generic-pae 
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic 
  linux-headers-3.2.0-29-generic-pae linux-headers-3.2.0-30 
  linux-headers-3.2.0-30-generic linux-headers-3.2.0-30-generic-pae 
  linux-headers-3.2.0-31 linux-headers-3.2.0-31-generic 
  linux-headers-3.2.0-31-generic-pae linux-headers-3.2.0-32 
  linux-headers-3.2.0-32-generic linux-headers-3.2.0-32-generic-pae 
  linux-headers-3.2.0-33 linux-headers-3.2.0-33-generic 
  linux-headers-3.2.0-33-generic-pae linux-headers-3.2.0-34 
  linux-headers-3.2.0-34-generic linux-headers-3.2.0-34-generic-pae 
  linux-headers-3.2.0-35 linux-headers-3.2.0-35-generic 
  linux-headers-3.2.0-35-generic-pae linux-headers-3.2.0-36 
  linux-headers-3.2.0-36-generic linux-headers-3.2.0-36-generic-pae 
  linux-image-3.2.0-25-generic linux-image-3.2.0-25-generic-pae 
  linux-image-3.2.0-26-generic linux-image-3.2.0-26-generic-pae 
  linux-image-3.2.0-27-generic linux-image-3.2.0-27-generic-pae 
  linux-image-3.2.0-29-generic linux-image-3.2.0-29-generic-pae 
  linux-image-3.2.0-30-generic linux-image-3.2.0-30-generic-pae 
  linux-image-3.2.0-31-generic linux-image-3.2.0-31-generic-pae 
  linux-image-3.2.0-32-generic linux-image-3.2.0-32-generic-pae 
  linux-image-3.2.0-33-generic linux-image-3.2.0-33-generic-pae 
  linux-image-3.2.0-34-generic linux-image-3.2.0-34-generic-pae 
  linux-image-3.2.0-35-generic linux-image-3.2.0-35-generic-pae 
  linux-image-3.2.0-36-generic linux-image-3.2.0-36-generic-pae lirc setserial 
0 packages upgraded, 61 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,001 MB/1,001 MB of archives. After unpacking 3,429 MB will be used.
Do you want to continue? [Y/n/?] **Y**
Media change: Please insert the disc labeled 'Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)' into the drive '/cdrom/' and press [Enter].


Selecting "Y" results in an endless loop of strings saying Media Change: Please insert the disk lableled . . .and press [Enter].

---

### Post by CharlesA on 2013-02-14
Sounds like your sources.list is messed up.

---

### Post by Mark_in_Hollywood on 2013-02-14
I don't see a problem, but as I recall the OS makes the fstab and (sorta) not the fstab makes the OS.

```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
## deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
## deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
## deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
## deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
## deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## Lines 5 and 6 of spotify commented out by mp on 15-jan-13
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
## deb-src [http://repository.spotify.com](http://repository.spotify.com) precise main
## deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free

## I notice that the repos are labeled: oneiric!
## This line and 3 following commented out by mp on 15-jan-13
## This line and the following two lines added by mp on 14-jan-13
## deb [http://ppa.launchpad.net/tfylliv/dvbhdhomerun/ubuntu](http://ppa.launchpad.net/tfylliv/dvbhdhomerun/ubuntu) oneiric main
## deb-src [http://ppa.launchpad.net/tfylliv/dvbhdhomerun/ubuntu](http://ppa.launchpad.net/tfylliv/dvbhdhomerun/ubuntu) oneiric main


## this line and following two lines added by mp 21-jan-2013
## on aptitude update lines below FAIL - commented out 21-jan-2013
## 2 lines below, had the ## removed by mp 14-feb-13
deb [http://ppa.launchpad.net/tfylliv/dvdhomerun/ubuntu](http://ppa.launchpad.net/tfylliv/dvdhomerun/ubuntu) precise main
deb [http://ppa.launchpad.net/tfylliv/dvdhdhomerun/ubuntu](http://ppa.launchpad.net/tfylliv/dvdhdhomerun/ubuntu) precise main

## added 14-feb-13 by mp - this is the repo for the barry blackberry
deb [http://download.barry.netdirect.ca/barry-latest/](http://download.barry.netdirect.ca/barry-latest/) ubuntu1204 main
```

---

### Post by CharlesA on 2013-02-14
> **Mark_in_Hollywood said:**
> I don't see a problem, but as I recall the OS makes the fstab and (sorta) not the fstab makes the OS.

```

deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

```

Problem line. Comment it out (add a # before the line) and rerun this:

```
sudo apt-get update && sudo apt-get install -f
```

This has nothing to do with fstab. ;)

---

### Post by Mark_in_Hollywood on 2013-02-15
I commented out the cddrom line.

ran aptitude install -f again, terminal said much the same, 

need to d/l 1 gig of updates, after install 3 gig (more) used. I went for it. An hour later, the updated kernels are all there. 

Now, how do I remove them? Three gig is still 3 gig.

I found this article particularly effective, as the author guides me through it, one step at a time.

[Remove Old Kernels In Ubuntu With One Command]("http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/")

After another hour or 90 minutes of watching aptitude do it's magic, the old kernels were gone and I had recovered valuable space in /sda3.

A portion of the run is pastebin'd here:

[http://pastebin.com/bmAKW3C5](http://pastebin.com/bmAKW3C5)

aptitude would check everything very thoroughly, remove one kernel, clear dependencies hurdles (if any) and then with each removal would generate a new grub.cfg. I thought the process would crash before it did all this, but, this IS Linux and not another name-brand OS. So aptitude worked flawlessly.

I'm writing up another post about this mess with the subject line: 

Apt-Get versus Aptitude Kernels Installed and Uninstalled

one old kernel didn't uninstall and in true heroic form, aptitude explained it in terms I dont' know, but I know the people here do. And I'm finally going to get the GRUB Recover mode screen back. 

Thank you all, very much. And especially you, Mr. Torvalds.

---

### Post by Bucky Ball on 2013-02-16
> **Mark_in_Hollywood said:**
> 
ran aptitude install -f again, terminal said much the same, 

 

Great that you got things solved, etc, but as I said a million posts ago, why are you using this command? Use the one suggested by CharlesA. ;)

---

