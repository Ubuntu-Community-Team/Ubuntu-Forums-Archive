---
title: "ATI Video Card Problem on Ubuntu 16.04 (Can't play videos)"
date: 2016-09-01
forum: New to Ubuntu
---

### Post by robertoperonista123 on 2016-09-01
Hi! I installed ubuntu 16.04 on my computer and I'm having problems to play video (youtube don't videos don't work and video files neither). So the way I see it can have something to do with 2 things:

1) When I first put Ubuntu cd to install it, at first I got a black screen, so I had to change something about "nomodeset" (I googled it but know I can't remember exactly what I did).

2) I know this version of ubuntu has a driver problem with mi video card ATI 5770 HD Radeon, apparently the old driver doesn't work anymore, but I think I should be able to play videos on youtube and things like that...

Help? 
Thanks!

---

### Post by mörgæs on 2016-09-03
Hi, welcome to the fora.

Have you considered installing a lighter Buntu, say X/Lubuntu?

---

### Post by robertoperonista123 on 2016-09-03
> **mörgæs said:**
> Hi, welcome to the fora.

Have you considered installing a lighter Buntu, say X/Lubuntu?

Hi, why would I consider that? The only thing I want to do is to be able tu play videos, and my video card is good enough, it should be possible to watch videos with Ubuntu's full version I think. But maybe you know something I don't..

---

### Post by Geoffrey_Arndt on 2016-09-04
Xubuntu or Lubuntu 16.04 should make a good fit for your system . . . speed and more capabilities re media playback.  Be sure to do these tweaks to optimize your system (especially #14 &15 re videos).

PS:   "But maybe you know something I don't" . . . . ah, . . . . are you kidding Mr. 2 Beans? 
[URL="http://www.noobslab.com/2016/04/important-20-tweaksthings-to-do-after.html"]
http://www.noobslab.com/2016/04/important-20-tweaksthings-to-do-after.html[/URL]

---

### Post by mastablasta on 2016-09-06
under testing the driver:

[SIZE=2]https://help.ubuntu.com/community/RadeonDriver
[/SIZE]

> To look for boot messages/errors, check 
```
dmesg | egrep 'drm|radeon'
```
To see your OpenGL information, you can run the commands below. Make sure your OpenGL renderer string does not say "software rasterizer" or "llvmpipe" because that would mean you have no 3D hardware acceleration: 
```
sudo apt-get install mesa-utils
LIBGL_DEBUG=verbose glxinfo
```

copy and paste these commands into terminal and let us know what you come up with (you cna copy the rtesult and post back here using the code tags - the # icon in advanced answer).

HD 5770 should be good enough to play videos and games.

option no. 2 is to use ubuntu 14.04 (not 14.04.5 or anything like that) and load the fglrx drivers which i think should still be available for this chip in that version. 

my initial suspicion is that you somehow disabled the chips hardware acceleration by using nomodeset.

---

### Post by grahammechanical on 2016-09-06
When you installed Ubuntu did you tick the box labeled "Install third party software?"  When we tick that box we get some very useful audio & video codecs that are free to download and use but are nonetheless proprietary software. Non-free in the sense of not being open source.

Without those audio & video codecs certain types of audio & video files will not play. Those codecs come in a package called Ubuntu Restricted Extras. If those codecs were not installed as part of the installation of Ubuntu then this command will install them.

```
sudo apt install ubuntu-restricted-extras
```

Regards

---

