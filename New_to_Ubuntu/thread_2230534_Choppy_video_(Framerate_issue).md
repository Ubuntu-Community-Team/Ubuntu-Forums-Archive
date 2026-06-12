---
title: "Choppy video (Framerate issue?)"
date: 2014-06-19
forum: New to Ubuntu
---

### Post by icelechi2 on 2014-06-19
When I play videos, particularly HD videos, I get choppy, skippy lines in them

Does anyone have this problem?

Is there any way to get around this?

Thanks.

---

### Post by yancek on 2014-06-19
You are not likely to get any useful suggestions as you haven't given enough information for anyone to do more than guess.

You are using Ubuntu, correct?  Which release of Ubuntu?  What hardware do you have, processor, RAM, video card and how old/new is the computer.
What vido player are you using?  VLC, MPlayer, something else?
What do you mean by HD videos?  Video clips on your hard drive?  Commercial movies you have on the Drive?
Answering these questions would be a start if you still need help.

---

### Post by icelechi2 on 2014-06-20
Sorry about that. I'm a bit of a beginner.

**Laptop:** HP Pavilion TouchSmart 15-n065sa
**OS:** Ubuntu Gnome 14.04
**Processor:** Intel Core i5 4200u
**RAM:** 8GB
**HDD:** 750GB HDD
**Graphics:** Intel HD Graphics 4600
**Monitor:** HD WLED BrightView Touchscreen

By HD videos, I mean any video above 480p.
This happens when I am playing videos saved on the hard drive and streamed videos.
It happens when I use VLC, Gnome-Mplayer, Parole and Totem.

Thanks

---

### Post by papibe on 2014-06-20
Hi icelechi2.

That looks like tearing.

Could you open a terminal, run these commands, and post back the results (you can copy/paste the text)?
```
uname -a

lspci -nnk | grep -iA2 vga

apt-cache policy libsdl1.2debian
```
Regards.

---

### Post by icelechi2 on 2014-06-21
[FONT=arial][SIZE=2]**uname -a**
Linux ubuntu-gnome 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

[/SIZE][/FONT][FONT=arial][SIZE=2][/SIZE][SIZE=4][/SIZE][SIZE=3][/SIZE][SIZE=2][SIZE=2]**lspci -nnk | grep -iA2 vga**
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)
	Subsystem: Hewlett-Packard Company Device [103c:2163]
	Kernel driver in use: i915

[/SIZE][B][SIZE=2]apt-cache policy libsdl1.2debian[/SIZE]


[/B][/SIZE][/FONT][FONT=arial][SIZE=2]libsdl1.2debian:
  Installed: (none)
  Candidate: 1.2.15-8ubuntu1
  Version table:
     1.2.15-8ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
[/SIZE][/FONT]

---

### Post by papibe on 2014-06-21
Thanks.

According to [this]("https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/1280665") and [this]("http://ubuntuforums.org/showthread.php?t=2219091&highlight=intel+tearing"), that library should solve tearing problems with the Intel driver on 14.04.

To install the library:
```
sudo apt-get update

sudo apt-get install libsdl1.2debian
```
Hope it helps. Let us know how it goes.
Regards.

P.S.: I'm not sure if you need to restart after that, so do that if it makes no difference initially.

---

### Post by icelechi2 on 2014-06-22
Thanks for the response. I installed it and restarted but the problem remains.

---

