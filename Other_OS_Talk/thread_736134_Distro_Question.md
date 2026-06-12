---
title: "Distro Question"
date: 2008-03-26
forum: Other OS Talk
---

### Post by hikujk123 on 2008-03-26
Which linux distro has the best wireless support?   I would like to use ubuntu/gOS on a desktop but need support for my linksys wireless usb adapter (which no ubuntu-based distro gives).  I am an xubuntu user and would like to install linux on an other desktop.

---

### Post by fatality_uk on 2008-03-26
Out the "box", I have found Ubuntu to have the best all round support. There's onl been one wireless device that it hasn't found.

---

### Post by hikujk123 on 2008-03-26
I have tried gOS (which is based on ubuntu) and the card can see networks but not connect.

---

### Post by Lostincyberspace on 2008-03-26
I know open suse has pretty good wireless support but you have to change your thinking to figure it out.

---

### Post by notwen on 2008-03-26
I would say Ubuntu/Mint or maybe SuSe has the better hardware recognition(including wireless), but why avoid the problem, when you could simply address it and resolve it?  Name your wireless USB dongle and let's see if we can help you get it running in whatever distro you prefer(Xubuntu).

---

### Post by tubasoldier on 2008-03-26
Perhaps the better question would be which HARDWARE supports Linux better? With the software available you can get any supported card working. Some distros just take more work. 

So the question is: Does the Linksys usb wireless have native linux drivers?
It probably doesn't and we all know ndiswrapper is a real crapshoot compared to native drivers.

---

### Post by Dragonbite on 2008-03-26
I found openSuse very good at hardware detection.  I have a Broadcomm wireless adapter in my laptop and in openSuse it takes running (while connected through some other means)```
install_bcm43xx_firmware
```It worked.

It can't hurt to look on openSuse's Wiki *AND* Ubuntu's *AND* Fedora's to find out how each one addresses the same situation and come up with whatever method works for you.

---

### Post by hikujk123 on 2008-03-26
I am going to try openSUSE.  If the card is not supported, I'll stick with ubuntu and make a post in Absolute Beginner Talk.  Thanks for the suggestions.

---

### Post by lavinog on 2008-03-26
I had a microsoft wireless card that was supported by ubuntu, but not microsoft. Microsoft won't even let you download the driver anymore. The page for it just explains that they only support things for 10 years...the card was less than 5 years old though.

---

### Post by Lostincyberspace on 2008-03-26
that's five years in computer time like 30 seconds real time

---

### Post by Bachstelze on 2008-03-26
Moved to Other OS Talk.

---

### Post by igknighted on 2008-03-27
Fedora 9 beta is using a 2.6.25 (pre-release, of course) kernel that has the full set of drivers for the new mac80211 wireless stack.  Might be a pretty good one to try.

---

### Post by Dragonbite on 2008-03-27
> **igknighted said:**
> Fedora 9 beta is using a 2.6.25 (pre-release, of course) kernel that has the full set of drivers for the new mac80211 wireless stack.  Might be a pretty good one to try.
You'll have time to fool around with things some, but if it doesn't work the first time you don't have to wait for latest version to try:[INDENT]Ubuntu 8.04 is due out Thursday April 24, 2008.
Fedora 9 is due out Tuesday April 29, 2008

openSuse 11 isn't due until Thursday June 19, 2008.[/INDENT]Though I have had better luck with openSuse's hardware detection than the others.  At the computer club meeting we tried installing Ubuntu, CentOS (RedHat) and openSuse on a server and openSuse was the only one that detected everything (on failed on the RAID, the other on the CD-Rom or something like that)

---

### Post by artilec on 2008-03-27
fedora 9,  The newer kernel offers more hardware support for wireless.

---

### Post by JawsThemeSwimming428 on 2008-03-27
Mepis, without a doubt! 

[http://www.mepis.org/](http://www.mepis.org/)

---

