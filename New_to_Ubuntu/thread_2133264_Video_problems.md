---
title: "Video problems"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by jeffvanderdoes on 2013-04-07
Hi,

I'm struggling a bit over the last few weeks with my Ubuntu 12.10 installation.  After a few minutes after logging on the video scrambles and get corrupted at which point I have to do a hard restart.   I have been able to keep current with software updates (got to move quick and get it started before video messes up but I can tell it is still processesing and finishes in the background).  I've tried to look through the Ubuntu forums but am just learning Linux and am not sure what to do next.  The machine is an older desktop Dell GX620 and has Intel 82945G Express Video processor.  I've tried going back a few versions on grub menu but it seems the problem still occurs.  I'm exploring reinstalling but if there's an alternative I'd sure like to try it?  Wondering if there are logs to check or ability to reinstall the video driver?  One other thing on one message in this forum some suggested meaybe a memory problem.  I ran through the memory checker and didn't find any problems.

Thanks for any ideas.

Jeff

---

### Post by agent-squirrel on 2013-04-08
Have you just tried running a live disk for a while. If the problem still exists then it could be a hardware issue, your video card may have failed.

---

### Post by ppjdee on 2013-04-08
[http://ubuntuforums.org/showthread.php?t=2128691&highlight=intel+graphics+problems+ubuntu+12.10](http://ubuntuforums.org/showthread.php?t=2128691&highlight=intel+graphics+problems+ubuntu+12.10)

you can try reading that, maybe it pertains to you.
have you tried changing or updating your gfx card driver in additional software?

---

### Post by fantab on 2013-04-08
> **jeffvanderdoes said:**
> Hi,

... After a few minutes after logging on the video scrambles and get corrupted at which point I have to do a hard restart. 
... The machine is an older desktop Dell GX620 and has **Intel 82945G Express Video processor**. ...

If I am not mistaken then your Graphics must be Intel GMA900 ([read here]("http://www.linwik.com/configuring_the_intel_graphics_media_accelerator_900-950_for_linux") for linux related info). It should work by default/out of the box on Linux as it has good open-source support. If the issue is 'motherboard' related then sometimes updating your mobo bios helps resolve issues. 

Also, reinstall **xserver-xorg-video-intel** package. You can do this with Synaptic Package Manager.

[ATTACH=CONFIG]241103[/ATTACH]

If that doesn't help then try to run Ubuntu with LiveCD/USB for a while and see if the problem persists in Live Mode as well. If it does then probably you need get your Mobo diagnosed.

**EDIT**: Do you have a SWAP partition on your HDD for Ubuntu?

---

### Post by jeffvanderdoes on 2013-04-27
All,

I tried reinstalling xserverxorg-video-intel pkg with same issue.  I tried running live mode and same issue. However, in XP side I never have any problems.  I decided to try upgrading to 13.04 (poor choice on my part).  Midway through it messed up.  I'm trying now to install 13.04 fresh.  We'll see what happens.

Not sure how to mark this thread closed.

Thanks,
Jeff

---

### Post by Mark Phelps on 2013-04-28
> **jeffvanderdoes said:**
> ... However, in XP side I never have any problems...
Windows uses very different video drivers from Linux and does not use an X-server.  It has nothing in common with Linux in terms of video drivers or video performance.

---

