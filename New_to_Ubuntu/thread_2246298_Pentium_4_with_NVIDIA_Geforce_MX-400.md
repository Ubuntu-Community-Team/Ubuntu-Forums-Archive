---
title: "Pentium 4 with NVIDIA Geforce MX-400"
date: 2014-09-29
forum: New to Ubuntu
---

### Post by robergto on 2014-09-29
Hi forum!
I appreciate your concern and ideas.-
I have just installed Xubuntu 14.04 in a Pentium 4 2800 machine, with Asus P4GE-MX Motherboard and a graphic card, NVIDIA GEFORCE MX-400. Xubuntu installed with no problems(I guess =D ), I have partitioned the disk (20GB) with the following scheme: 1_7 GB for / (root so far a I know) ; 2_3 GB Swap ; 3_10 GB HOME. I hope it is correct, the system didn't complain. Thing is that some weird thing goes on with graphics. The kinnda get lost. They exist there, when I hover with the mouse pointer they reappear, sometimes they stay, sometimes just for a glance. If there is a list, for instance, it is not shown, and if I scroll down, it suddenly appears. If I open file manager I must hover over the entire windows to discover if something is there, or if I open a console it just does not show anything until I move it, or change the window and come back to it.-
There are more things, like the mouse would stop moving and I have to unplug it and plug it again. None of this things happened with windows XP SP3, which was installed on that disk.-
Thanks in advance for your help, hope you have some ideas to throw!

:p

---

### Post by kurt18947 on 2014-09-29
I have a Y2K 667 Mhz. Celeron with a similar video card that I'm playing with.  Xubuntu worked but had graphics issues like you're seeing. It appears to me - certainly no expert - that Xorg or the open video driver on *buntu has issues with older Nvidia cards. I tried Lubuntu and it was worse.  I tried Bodhi, the graphics were unusable.  I experimented with some live DVDs and finally settled on MX14, an offshoot project associated with Mepis using Debian testing instead of some Slackware flavor. 

 It uses an XFCE desktop that looks different than Xubuntu but there are similarities.  It may be closer to Xubuntu 12.04's desktop.   It's advertised as mid-weight but it seems pretty light.  It seems to come with Flash and audio codecs installed. I doubt it has the support available that the *buntu versions have but both being Debian based there are quite a few similarities between *buntu & MX14.

---

### Post by robergto on 2014-09-29
Hey! Thanks for your help, indeed.-
Say, I am a COMPLETE newbie to linux. Guess I quite understand your response. As far as I THINK I get it( =D ) your're talking of another distribution of linux. Is that so? Does it mean that there is no way of downloading proper drivers and stuff to get it working like it should? To state my point(of being a newbie), I downloaded some NVIDIA-Linux-96-and-so-on.run Got absolutely lost. You know, WINDOWS -> Double click =P I could not get quite how to set it up(so far I guess that I have to shut down a called X server, and open the run from the root, but cannot even imagine how, and been searching and got even more confused).-
Again, thanks for your advice, I was thinking, also, on Free BSD, but I'm kinnda lost.-

(Y)

---

### Post by mörgæs on 2014-09-30
How does it work in a live boot of Xubuntu 12.04?

---

### Post by kurt18947 on 2014-09-30
> **robergto said:**
> Hey! Thanks for your help, indeed.-
Say, I am a COMPLETE newbie to linux. Guess I quite understand your response. As far as I THINK I get it( =D ) your're talking of another distribution of linux. Is that so? Does it mean that there is no way of downloading proper drivers and stuff to get it working like it should? To state my point(of being a newbie), I downloaded some NVIDIA-Linux-96-and-so-on.run Got absolutely lost. You know, WINDOWS -> Double click =P I could not get quite how to set it up(so far I guess that I have to shut down a called X server, and open the run from the root, but cannot even imagine how, and been searching and got even more confused).-
Again, thanks for your advice, I was thinking, also, on Free BSD, but I'm kinnda lost.-

(Y)

Yes, MX14 is a linux distro completely unrelated to Ubuntu except that underpinnings are based on some version of Debian.  I tried Xubuntu (which was usable but not right), Lubuntu, Bodhi and one or two others with Ubuntu roots.  I couldn't get the video to display properly with any of them.  I sort of suspected that the problem lie with Xorg and I might have been able to tweak a config file and get *buntu to work but that's beyond my knowlege.  The machine I was working with is probably two generations older than your P4 which didn't help.  There are linux video drivers available for Nvidia & AMD/ATI but I doubt they support the chipsets we have.  If there are manufacturer provided video drivers, they'd be found under 'additional drivers' which I *think* are found in 'software & updates'. There's a button labeled "check for drivers" or similar.  Click it and see if anything is found.   I don't have a copy of Xubuntu handy to check.  One significant difference between Windows & Linux is that any CD/DVD provided likely doesn't contain linux drivers.  Drivers are either built into the kernel or available via a repository.  Even if there are linux drivers on a manufacturer provided disk, they may be outdated or need to be compiled first before installing.

---

