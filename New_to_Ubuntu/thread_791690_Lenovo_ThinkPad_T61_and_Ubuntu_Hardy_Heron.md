---
title: "Lenovo ThinkPad T61 and Ubuntu Hardy Heron"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by variableenigma on 2008-05-12
I'm really not sure where to put this question, but since I'm pretty much a beginner (kind of), I'll try here..

I'm planning on getting a new laptop and I want to run Ubuntu ONLY.

The most important applications to me are Firefox, World of Warcraft, and Natural Reader (a Windows text-to-speech program). I want to be sure that those programs will work properly with my new computer running Ubuntu (and Wine for the Windows applications).

The one I'm looking at is a Lenovo ThinkPad T61 15" Widescreen. The specifications I like (and can afford) are as follows:
Intel® Core™ 2 Duo processor T8300 (2.4GHz 800MHz 3MBL2)
15.4 WXGA TFT
NVIDIA Quadro NVS 140M (128MB)
3 GB PC2-5300 DDR2 SDRAM 667MHz SODIMM Memory (2 DIMM)
UltraNav (TrackPoint and TouchPad)
160GB Hard Disk Drive, 7200rpm
CD-RW/DVD-ROM Combo 24X/24X/24X/8X Max, Ultrabay Slim
ThinkPad 11a/b/g Wi-Fi wireless LAN Mini-PCIe US/EMEA/LA/ANZ
6 cell Li-Ion Battery

What are your thoughts?

---

### Post by Het Irv on 2008-05-12
Your specs look good, you shouldn't have any problems.  I would do some research on the wifi card just to make sure.  

EDIT: Found this> My choice would be atheros-based... Call me biased, but I've found they perform better with greater stability than intel cards. Don't anyone knock me because of this, just my point of view. Plus you get a 13th channel on the atheros card that you don't have on an intel card. That's why the "Thinkpad a/b/g" is labeled US/EMEA/LA/ANZ (i.e, North America, Europe/MiddleEast/Asia, Latin America/Australia-NewZealand). Many places outside North America make extensive and exclusive use of the 13th channel (d-mode switch ... so, in fact, you have a/b/d/g)

Go to [www.google.com/linux](www.google.com/linux) (it's google that searches only linux-related sites and info) and type in intel 4965 or intel 3945 and "reception". See what pops up.

It all really depends on the choice of linux distro you'll install. If you "Ubuntu" your system, then you won't have a problem with either. If you install gentoo or slackware, then good luck getting intel cards to work right. If you install Fedora, then you may have some trouble with atheros cards (because of the change from madwifi to ath5k).... It's all in a distro.
Rolling Eyes
[http://forum.thinkpads.com/viewtopic.php?p=410686&sid=f7dff0aeb6e7c820016f0a4a6b56f97e](http://forum.thinkpads.com/viewtopic.php?p=410686&sid=f7dff0aeb6e7c820016f0a4a6b56f97e)


As for the apps, well Firefox comes preinstalled, 8.04 comes with Firefox 3 Beta 5, and not all plugins work for it yet, so that may be a problem if you are used to running a bunch of plugins.  If you have a list, post it and I can look for you.

Wine:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

WoW should work, but I am not sure about Natural Reader.

---

### Post by variableenigma on 2008-05-12
Great! Thanks for your thoughts. :)

I run Ubuntu Hardy on a Dell Latitude D620 right now. 

Firefox is fine, I'm not too concerned about plugins. Being able to get a good internet connection is definately important, and it doesn't seem like that will be an issue.

As for Wow, I KNOW it won't work on my Dell for several reasons- mainly because of the Intel grahics card and extremely low framerate (to the point of crashing) in d3d. I know that nVidia cards have better success with Ubuntu and Wine and gaming than the Intel cards do, so I'm hoping that that will help.

And Natural Reader.. Well, I don't have the full program yet, but I did install the demo version on Wine. I don't think I'll be able to have text read directly through the program because it doesn't recognize linux audio drivers, BUT, the full version has a text-to-mp3 feature that I think will work fine.

---

