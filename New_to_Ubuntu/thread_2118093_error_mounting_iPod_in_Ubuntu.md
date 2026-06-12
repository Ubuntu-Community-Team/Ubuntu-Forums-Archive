---
title: "error mounting iPod in Ubuntu"
date: 2013-02-20
forum: New to Ubuntu
---

### Post by tlalokman on 2013-02-20
Hi,

I've seen other posts about errors mounting iPod in Ubuntu but the message it appears to me is different. I'm an absolute begginer in Linux so I would appreciate all your help.

Some context: yesterday, I was listening my music in the iPod when suddenly it just stopped. When I saw the screen there was a message saying that I had no music, no videos, nothing. And 0kb free!!! Full, but empty! WTF?!!!

So I decided to see if my music was still there and I connected it to my computer running with Linux (before, I had never done that because I had another computer that I sold, so I never synced the iPod anymore). And when I connect the iPod through the USB cable, I see this message:

                     P { margin-bottom: 0.21cm; }   Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb2, 
        missing codepage or helper program, or other error 
        In some cases useful info is found in syslog - try 
        dmesg | tail  or so
  
Can you help me? Do you know why it happened? Do you think I can recover my music? What's wrong with the iPod? 

I work with Ubuntu 12.04 LTS and it is a 120 GB iPod classic (an "old" one)

Thanks a lot for your help!

---

### Post by bigmonmulgrew on 2013-02-20
Ok for starters if it spontaneously says it has 0kb left it sounds like the hard drive has died.

I don't have an ipod myself. I looked into syncing a few years ago for my sister. At the time you need itunes to connect and setup your ipod and after that you can manage your library with quite a range of programs. The issue there is you need itunes for first setup. You also find that 3rd party software has nothing to help with issues on the ipod. 

Really I think its dead but if not your best chance to revive it is going to be with itunes in windows. If its already possibly dead you don't want to make it worse by using unofficial software.

If the ipod is dead you will just have to re-download the music

Also on a personal note, get something cheaper than an ipod. Your paying way over the odds for a decent music player and other brands can be managed with pretty any software you like.

I can recommend some music players if you decide to give up on the ipod.

---

### Post by tlalokman on 2013-02-20
Hi, bigmonmulgrew

Thanks for your response. 

If it is dead, does that mean it won't work again? Can I fix it? I don't want to buy a new one, and of course I would consider cheaper options that you may suggest, but if I would rather prefer using again this device, if it is possible.

I'm going to a cybercafe to try to mount it in iTunes and I'll tell you the result.

---

### Post by fuorviatos on 2013-02-20
> P { margin-bottom: 0.21cm; }   Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb2, 
        missing codepage or helper program, or other error 
        In some cases useful info is found in syslog - try 
        dmesg | tail  or soI won't bet it's dead, at least - not yet.
Can we see the output of ?
 > dmesg|grep sdb2

---

### Post by DiabolicalClaptrap on 2013-02-20
[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/522478](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/522478)

---

### Post by tlalokman on 2013-02-20
@[[COLOR=#000000]fuorviatos[/COLOR]]("http://ubuntuforums.org/member.php?u=1790176"): do you mean writing what you quoted in the Terminal while the iPod is connected through the USB cable?

@DiabolicalClaptrap: I'm sorry. I really don't get what I have to do by reading the thread you posted. Could you explain a little more?

---

### Post by DiabolicalClaptrap on 2013-02-20
> [Gordon Ball (chronitis)]("https://launchpad.net/%7Echronitis")             wrote             on 2011-01-25:                                                            [ #8]("https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/522478/comments/8")                                                               A workaround, at least for the second-generation iPod Nano, as of ubuntu 10.10 is to insert the following into /lib/udev/rules.d/90-libgpod.rules
 ENV{ID_VENDOR}=="*Apple*", ENV{ID_MODEL}=="*iPod*", ENV{ID_FS_LABEL}=="*iPod*", ENV{UDISKS_PRESENTATION_NOPOLICY}="1"
 This prevents any attempted mounting or handling of the the first  (system) partition on the iPod, after which the second mounts  successfully and is visible from, eg Rhythmbox.
 Only tested once and might interact badly with other iPod partition  arrtangements - presumably this is something that should be done  properly in the /lib/udev/ipod-set-info binary. 
Try these 1 by 1. If it doesn't work, revert changes.

in terminal:
nano /lib/udev/rules.d/90-libgpod.rules

> [John Stultz (jstultz)]("https://launchpad.net/%7Ejstultz")             wrote             on 2011-09-26:                                                            [ #10]("https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/522478/comments/10")                                                               Commenting out the following line from /lib/udev/rules.d/90-libgpod.rules seems to resolve this for me:
 ACTION=="add|change", SUBSYSTEM=="block", ENV{ID_FS_USAGE}=="filesystem", ENV{DEVTYPE}=="partition", ATTRS{idVendor}=="05ac", ENV{ID_MODEL}=="iPod", IMPORT{program}="/lib/udev/ipod-set-info $tempnode $attr{busnum} $attr{devnum}"

Same deal, but replace the bit after nano with /lib/udev/rules.d/90-libgpod.rules. nano is your editor.

---

### Post by fuorviatos on 2013-02-20
> **tlalokman said:**
> @[[COLOR=#000000]fuorviatos[/COLOR]]("http://ubuntuforums.org/member.php?u=1790176"): do you mean writing what you quoted in the Terminal while the iPod is connected through the USB cable?

Yep. This will help us to make sure your Ipod gets recognized correctly by the system and thanks to this we should be able to figure out why it doesn't get mounted.

> @DiabolicalClaptrap: I'm sorry. I really don't get what I have to do by reading the thread you posted. Could you explain a little more?He has just pointed you to a bug on Launchpad which will probably get patched in the new version of ubuntu.

---

