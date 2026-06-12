---
title: "What's the point of upgrading from LTS to a .10 update?"
date: 2014-11-01
forum: New to Ubuntu
---

### Post by Benjamin5th on 2014-11-01
I'm just thinking and trying to understand Ubuntu, and I've come across something I find confusing.

If (for examples sake) I run 12.04 LTS, and it continues getting updates, why would I upgrade to anything but the next LTS 14.04? Wouldn't 12.04 get all the support and updates in in 12.10, 13.04, etc? 

I'm sure there is a good reason I'm not seeing, hopefully you can shed some light? :)

---

### Post by howefield on 2014-11-01
LTS releases will indeed get security updates to your installed packages, but won't get updated versions.

Interim release generally have newer packages and possibly features not found in previous releases.

---

### Post by sammiev on 2014-11-01
If everything is working, don't break it.

---

### Post by grahammechanical on 2014-11-01
Some Linux distributions bring out a new release when its developers make up their minds that the release is ready. It was decided a long time ago go that Ubuntu would be released every 26 weeks in April and October. This has meant that users get the benefit of the continued development of Ubuntu sooner than rather than later.

The version of Ubuntu that came out at the end of April 2004 (12.04 Long Term Support) got 5 years support for the desktop instead of the 3 years support that previous Long Term Support (LTS) versions got. This makes the LTS version ideal for those users who are happy with things as they are. Business users especially do not want to invest the employee time in upgrading their many machines or giving training to employees who are not familiar to the changes made in Ubuntu.

It does seem that the Interim releases with only 9 months support are less necessary than they used to be. Ubuntu 14.04 has big improvements to the Unity user interface compared to Unity in 12.04. And Ubuntu 14.10 has the same version of Unity as 14.04 (version 7). As will Ubuntu 15.04 have. From the user interface point of view there does not seem much reason for going onto the next three Interim releases.

Six monthly releases are a tradition in Ubuntu. The developers have to follow tradition. Ubuntu users do not. If you want stability install an LTS release.

By the way, since no body has mentioned it, I will. If you are on Ubuntu 12.04 you cannot upgrade to 12.10 and 13.04 and 13.10. They have all reached end of life, no support. Our choice is either to get on an LTS and stay there for at least 2 years or upgrade every six months or so.

Regrads

---

### Post by yancek on 2014-11-01
> The version of Ubuntu that came out at the end of April 2004 (12.04 Long Term Support)

Typo?  Should be April, 2012.  If everything is working, I can't see much reason to update unless some new or improved software you want is available with a new release.

---

### Post by Benjamin5th on 2014-11-02
Ah, okay. Thanks for clearing that up for me :)

---

### Post by riverguy99 on 2014-11-02
If you are running 12.04 and having no problems with it, KEEP IT!  It's rock solid and dependable.  It also does not carry with it all the glitches that appear in 14.04.  I have yet to hear of any "imporovements" that make it worth while enduring all of the reported glitches with 14.04.  You'll hear this from every angle on this Forum:  "If it ain't broke, don't fix it!"

---

### Post by Bucky Ball on 2014-11-03
LTS for servers and production machines (that must be stable and dependable) the rest for testing. That's how I roll. For me, there is no reason to upgrade every six months. Can't afford the time or the possibility of downtime.

I use LTS and generally ween the next LTS in on another partition, then just drift across to it full-time as it gets solid (all my data is accessible from every install). 

I do have three spare 15Gb partitions, my 'playthings', which often have interim releases and other things on them.

---

### Post by mastablasta on 2014-11-03
> **riverguy99 said:**
> If you are running 12.04 and having no problems with it, KEEP IT!  It's rock solid and dependable.  It also does not carry with it all the glitches that appear in 14.04.  I have yet to hear of any "imporovements" that make it worth while enduring all of the reported glitches with 14.04.  You'll hear this from every angle on this Forum:  "If it ain't broke, don't fix it!"

well in KDE plasma is faster and there are many smaller improvements and optimisations.

most importantly my sound chip works properly more often than before. and with digital stereo sound whatever 

other than that... meh...

---

### Post by kurt18947 on 2014-11-03
The only good reason to upgrade to non-LTS releases IMO is hardware support. For example, I have a couple RealTek USB Wifi adapters that don't work reliably with 14.04 and earlier using the built-in driver, they need a patched version of RealTek's proprietary driver.  I used a 14.10 live USB and reliability seems improved so I installed 14.10 on its own partition. The RealTek wifi adapters are much more reliable than they've been so far, I haven't had one 'stall' for want of a better term for several days.  LTS get point upgrades i.e. 12.04.5, 14.04.1 and I think - not sure - that the point upgrades include newer kernels which should include better hardware support.  If not, I think it's possible to use a newer kernel in an older LTS release but I have no experience with that.

---

### Post by Bucky Ball on 2014-11-03
Yep. You can just install the .debs of the newer kernels. I had the 11.10 kernel running in 10.04 for awhile for some bit of hardware I was using.

---

