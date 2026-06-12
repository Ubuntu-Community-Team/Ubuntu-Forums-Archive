---
title: "Problem with security update"
date: 2017-04-23
forum: New to Ubuntu
---

### Post by pantazi on 2017-04-23
Brand new to Ubuntu and very limited knowledge of Linux.
Trying to squeeze more life from Vista laptop, I downloaded 14.04LTS from a disk made some time ago. All went well and despite my lack of experience, got it all up and running including setting up a wireless printer ( took me 8 hrs using the forum info, but I got there and learnt a little about the use of the terminal!).
However, a security update appeared, clicked install, and when finished, I had no wifi network.
Connected by ethernet and spent the next two days searching the forums/Google and entered many variations of 'solved' answers to no avail. I repeated the disk method and all went back to normal ,and I reset all preferences,very time consuming.
The question is:
The update nag has returned and I don't want to repeat another lost day, so do I ignore it, against my better judgement, or update to 16.04 LTS and hope the problem is cured?
The details of the update are: 'Current updates for your current Hardware enablement stack ended 2016-08-04 https:// wiki.ubuntu.com/1404_HWE_EOL

---

### Post by howefield on 2017-04-23
Sounds more like the HWE stack wants to upgrade the kernel and graphics stack rather than an actual *full* upgrade to 16.04.

What's the output of 

```
uname -r
```

and

```
cat /etc/*-release
```

---

### Post by pantazi on 2017-04-23
Thanks for reply, unfortunately my Terminal script is now not functioning correctly, the letters are merging into one another. Have rebooted but no joy.

Re your reply, I thought this was a security update, I didn't try to install 16.04.

```
uname -r didn't work but:
3.16.0-77-generic
rob@rob-HP-Compaq-6720s:~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"
NAME="Ubuntu"
VERSION="14.04.5 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.5 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
```

---

### Post by pantazi on 2017-04-24
Any advice please?

---

### Post by howefield on 2017-04-24
> **pantazi said:**
> Any advice please?

No advice to give really, it is a no brainer as far as I can see.

You are running on an unsupported HWE stack. So your choice is either to continue using a kernel which hasn't received security updates for some time and won't in the future or upgrade to the xenial stack as per the "upgrade nag" that you are seeing. You would still be on the Trusty series but with an HWE supported till 2019.

---

### Post by pantazi on 2017-04-24
Thanks for the info, understood.
I notice on the LTenablementStack wiki the following:

[h=3]Ubuntu 14.04 LTS - Trusty Tahr[/h] The  14.04.2 and newer point releases will ship with an updated kernel and X  stack by default. If you have installed with older media you can use  the following to install the newer HWE kernel derived from 16.04  (Xenial): 
 
[h=4]Desktop[/h]  sudo apt-get install --install-recommends linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial 

Would this be useful for me?  Alternatively I would go for a fresh 16.04 install

---

### Post by howefield on 2017-04-24
Yes, that's the command line way to upgrade the HWE. That should put the system back on track with regards support. I believe this is the last HWE for Trusty so you won't have to go through it again at a later date.

By the way and just for information, the 16.04 series of HWE are upgraded automatically from one to the other, if installing from a 1604.2 image or later.

---

### Post by Autodave on 2017-04-24
I would just get the 16.04 release and install that fresh.  You may also want to look at Xubuntu instead of Ubuntu: same OS with a simpler (less RAM usage) desktop. From what I found, that machine probably only has 1 gig RAM, so Xubuntu would be a better choice. Xubuntu will be quicker than Ubuntu because you will have more RAM available to run programs instead of the fancy desktop.

---

### Post by pantazi on 2017-04-24
Ok I get that and I appreciate your help. A steep learning curve for me after putting up with Windows for so long. (Willing to learn though!). My old laptop feels very fast now with Ubuntu and no Windows bloatware. Can mark as solved.

---

### Post by howefield on 2017-04-24
> **pantazi said:**
> Ok I get that and I appreciate your help. A steep learning curve for me after putting up with Windows for so long. (Willing to learn though!). My old laptop feels very fast now with Ubuntu and no Windows bloatware. Can mark as solved.

You are very welcome, marking the thread as solved can be done yourself by choosing the option from the Thread Tools menu near the top of the page.

---

### Post by pantazi on 2017-04-24
I was actually replying to Howefield, apologies and thanks to Autodave too.

---

### Post by pantazi on 2017-04-24
Thanks Autodave, I'll carry on as I am, but will investigate further if the laptop gives problems. I really don't want to spend my retirement sat at a computer.

---

### Post by Geoffrey_Arndt on 2017-04-24
The best way not to spend retirement in front of a computer, is to learn enough to have a simple, reliable version of Linux installed.    Investing in some learning time up-front pays dividends on the back end.    Installing most printers from HP to Epson to Brother should take anywhere from 2 minutes to an hour max.   But that's part of the learning curve - - - knowing what hardware is Linux friendly and what is not (for example, Canon & Lexmark printers are not).    Another absolutely critical thing to know is your hardware specs in detail, and then sharing those here at the forums as you describe any future "issue(s)" . . . 

I suggest you install the command line program "inxi" . . . and then run "inxi -Fx" to get a decent and concise summary of your hardware.    Most hardware is not "pre-designed & tested" for Linux, _as it certainly has to be for Windows_.    Hence these comments.

---

### Post by pantazi on 2017-04-25
Too true, you get out what you put in. Thanks for input.

---

