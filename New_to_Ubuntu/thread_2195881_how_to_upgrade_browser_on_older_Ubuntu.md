---
title: "how to upgrade browser on older Ubuntu"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by imatek1 on 2013-12-26
Hi - I am rebuilding some older desktops to donate to my friends project for military vets.   These PC are Pentium 4 and I got 768 or 1gb ram in them and had to use Ubuntu 11.04 , newer discs would not install,  so I got everything working BUT in firefox it says my browser is too old and needs to be updated ,  I downloaded the firefox .tar.bz2 file and the google chrome  .deb but cant figure out how to install them ,  am I wasting my time?    I tried the new Ubuntu in 32 bit , it wont install , only disc I got to work was this older version,  the users just need internet and office apps to work.  Internet seems OK for browsing but wont play any flash video or youtube due to old unsupported browser

any help?

hoping its an easy fix , I don't want to give them problem computers.  Why doesn't the browser just update normally like with windows,  why all the extra steps?

---

### Post by deadflowr on 2013-12-26
Firstly, have you tried a lighter distro like [Lubuntu]("http://lubuntu.net/"), or [Xubuntu]("http://xubuntu.org/")?
Either of those should install fine on the system(s) at hand.

Installing either of  those  browsers on unsupported OS may prove problematic in the long run.

---

### Post by imatek1 on 2013-12-26
thanks,  never heard of Lubuntu or Xubuntu , wil ltry it,  does it use a current browser that doesn't need updating via complicated installs?

---

### Post by deadflowr on 2013-12-27
They both run the same system as Ubuntu, underneath.
Both are basically lighter desktops.(LXDE, and XCFE)
Ubuntu uses unity, which is somewhat heavy.

---

### Post by vasa1 on 2013-12-27
> **imatek1 said:**
> ...  I downloaded the firefox .tar.bz2 file and the google chrome  .deb ...
I don't know about Firefox, but Google has a policy of not letting its current browser run on older versions of Linux: [https://support.google.com/chrome/answer/95411?hl=en](https://support.google.com/chrome/answer/95411?hl=en)

For Firefox, see [https://www.mozilla.org/en-US/firefox/26.0/system-requirements/](https://www.mozilla.org/en-US/firefox/26.0/system-requirements/) and google "firefox system requirements" for older versions.

---

### Post by mörgæs on 2013-12-27
I have collected some advice for dealing with old hardware. Might come in handy for you.
Please see the link in my signature.

---

### Post by Bucky Ball on 2013-12-27
As suggested above, 11.04 is NOT a good choice as it hasn't been supported for ages and has had no updates, including security, in a long while. Not good for ex-military personnel! :-k

As also suggested, newer browser probably won't work on it anyway. Xubuntu is an excellent choice and should install without issue on older machine (I am running it on my desktop which has a P4 and 1Gb of RAM). Faultless. Lubuntu will also install fine.

They both use the latest Ubuntu base kernel but have different sets of default apps and a different desktop environment (you'll likely not get the current Ubuntu DE Unity running on these older boxes).

As these are being given away and you will not be on hand, stick with LTS releases, the current, stable and reliable 12.04 LTS being your best choice. Supported until April 2015 on Xubuntu.

LTS releases are also a one-click (or maybe two or three) upgrade to the next LTS when that time arrives, leapfrogging the interim releases in between (12.04 upgrades directly to 14.04 next April rather than needing to upgrade, say, 12.10>13.04>13.10>14.04). 14.04 will then have another three year support (and can be upgraded directly to 16.04 LTS when that arrives).

---

### Post by imatek1 on 2013-12-28
installed LuBuntu and PC works, not faster but the flash on web pages actually shows up,  takes a long time for youtube videos to play BUT they play ,   looks like a WINNER ,  thanks

---

### Post by plurga on 2013-12-28
nice advices mörgæs , thanks.

---

### Post by deadflowr on 2013-12-28
> **imatek1 said:**
> installed LuBuntu and PC works, not faster but the flash on web pages actually shows up,  takes a long time for youtube videos to play BUT they play ,   looks like a WINNER ,  thanks
Yeah, it's basically the same under it, as I said, it just runs with lower resources.
(ie, less ram, less graphical heaviness, so on and so on)

---

### Post by Bucky Ball on 2013-12-28
Give the minimal install a go if you're involved with upgrading. That'll give slightly better results with a bit of planning and keeping it to essentials. In the meantime, nice it's working. Please mark thread as solved if you feel it is, to help others. ;)

---

