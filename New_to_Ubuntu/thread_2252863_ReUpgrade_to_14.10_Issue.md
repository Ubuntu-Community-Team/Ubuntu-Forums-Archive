---
title: "Re:Upgrade to 14.10 Issue"
date: 2014-11-15
forum: New to Ubuntu
---

### Post by perpetuum_mobile2 on 2014-11-15
Still a newbie here. I just upgraded to 14.10 today (some files showed 14.11.6). Now it boots to wallpaper only. I run no other software on this PC to interfere.
I did Ctrl-Alt-F1. I tried xfdesktop. It installed itself, 15MB of files. Tried xfdesktop: "Failed to parse arguments: Cannot open display:"
What can I do?

---

### Post by Sef on 2014-11-15
Moved to its own thread.

---

### Post by grahammechanical on 2014-11-15
If we upgrade to a newer version of Ubuntu and the OS does not load to a desktop or a working desktop, then installing an alternative desktop will not necessarily solve the problem. As proved by your experiment.

When Ubuntu loads to the wallpaper only there are a few things to try.

1) Right click the wallpaper and when a menu appears select Change Desktop Background. That will open System Settings and then we can load Software and Updates and in the Additional Drivers tab we can experiment with video drivers. I would suggest reverting to an open source video driver. A restart is necessary.

2) At the Grub boot menu select the Advanced Options for Ubuntu sub-menu and then select Recovery Mode. At the recovery menu select Resume. That will load to a desktop using an open source video driver as a fall back video driver. Then at the desktop we can change video drivers in Additional Drivers.

If the problem is not caused by the video driver then open an terminal and run

```
dconf reset -f /org/compiz/
```

That will reset the Compiz window compositor/ manager. Then we might try restarting Unity with

```
setsid unity
```

Regards.

---

### Post by perpetuum_mobile2 on 2014-11-15
Thank you for your help.
At 1st #1 "Right click the wallpaper" did not work. So I went with #2. It went ok until the "Additional Drivers". The message says that "No additional drivers available" and "No proprietary drivers are in use". The computer worked for a while as is, but crashed to a blank screen while I was away.
After reboot "Right click the wallpaper worked". The "Additional Drivers" route gave the same results as above. The screen does not allow anything other than "Close".
Note: The software shows ubuntu 14.04 LTS so the upgrade to 14.10, which I did before these problems, did not work.
I tried "Hardware" "Displays". It properly id'd Dell 20" and 1800x1440. I tried low res settings like 1240x1080. Rebooted. It worked bringing the menu back. Reset to 1800x1440 worked so far.
So thank you for your help, I was able to follow through to make it work.
Should I be worried that there are "no drivers available" ?

---

### Post by perpetuum_mobile2 on 2014-11-27
Unfortunately the problem restarts after each reboot. Everything works fine after I go through the awkward procedure in my previous post.
- How can I "save" the video settings to make them permament?
- If not how can I find a Linux video driver for Dell GX620 onboard video Intel media accelerator 950? (Google did not help)
- I used version 12.? for over a year and the default video driver worked fine. Is it possible to reload version 12.?

---

### Post by ptn107 on 2014-11-27
If you did the network upgrade that failed, may you consider upgrading from the 14.10 install disk?  Boot the 14.10 disk that you can download [_here_]("http://releases.ubuntu.com/utopic/ubuntu-14.10-desktop-amd64.iso").  Choose Install Ubuntu when prompted. When you get to the 'installation type screen' choose the top option 'Upgrade Ubuntu 14.04 LTS to Ubuntu 14.10'.  Software and settings will be kept where possible.  A clean install may also be in the cards for you if you cannot get this sorted out.
[IMG]http://i62.tinypic.com/fjf2id.png[/IMG]
Edit: Why is that so big??

---

