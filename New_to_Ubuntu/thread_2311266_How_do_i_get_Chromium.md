---
title: "How do i get Chromium?"
date: 2016-01-25
forum: New to Ubuntu
---

### Post by dan_williscroft on 2016-01-25
Hi,

I am a massive newbie to linux and ubuntu. I recently got a G5 powerpc that was collecting dust at work and decided to see what i could do with it. I installed ubuntu 12.04 lts and have herd about Chromium. When i try to install off software center it says not found. Ive tried using the sudo apt-get install chromium and all i get is this.....

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package chromium is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  chromium-bsu

Please help,

Thank you.

---

### Post by Geoffrey_Arndt on 2016-01-25
Are you running a 32 or 64 bit PC/OS?.    If 64, you're better off going to the Chromium website and search for "Canary" - -  a 64 bit version of Chromium.

BTW, both Google and Canonical are limiting the functionality of Chromium 32 bit in near future.   So, if you can, Ubuntu LTS 14.04 or even 15.10 might be a better option for getting current verisions of Chromium from the repos.

IF you're on an older machine, you might want to look at lighter Chrome based browsers anyway (the new Opera for example).

---

### Post by dan_williscroft on 2016-01-25
Cheers i will try and install a later version of ubuntu. Thanks for your help.

---

### Post by dan_williscroft on 2016-01-25
32 bit i think the only available version for my power pc is lubuntu 14.04, 15.10 is only available as a server

---

### Post by dan_williscroft on 2016-01-25
ubuntu mate is available in 15.04 whats the difference?

---

### Post by grahammechanical on 2016-01-25
You could try going to system settings>software sources and making sure that all the repositories are enabled including the partner repositories. Then see if software centre will install Chromium.

Ubuntu 15.04 and all flavours built from it such a Ubuntu Mate will reach end of life the beginning of February this year. So, your only options apart from 12,04 (support until April 2017) are a 14.04 or 15.10 based flavour of Ubuntu.

Ubuntu Mate has the Mate desktop environment. Lubuntu has the LXDE desktop environment. Different desktop environments are the difference between different flavours of Ubuntu.

My understanding of this news item is that 32 bit versions of Chromium are not affected by Google dropping support for 32 bit versions of Chrome. The change takes place in March so you should still be able to install Chromium. Check to see if all the software repositories are enabled.

[http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued](http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued)

Regards.

---

### Post by Geoffrey_Arndt on 2016-01-25
Multimedia support for proprietary formats (netflix, hulu) etc. are in the future, only supported via Chrome 64b.   So, if that kind of streaming is important, the 32 bit version of Chromium will be lacking also.    It seems in general, 32 bit OS support is waning in all kinds of services and programs . . . but, nothing stands still.

---

### Post by deadflowr on 2016-01-26
> **Geoffrey_Arndt said:**
> Multimedia support for proprietary formats (netflix, hulu) etc. are in the future, only supported via Chrome 64b.   So, if that kind of streaming is important, the 32 bit version of Chromium will be lacking also.    It seems in general, 32 bit OS support is waning in all kinds of services and programs . . . but, nothing stands still.
 fyi, hulu no longer works in chrome or chromium.

That said, the chromium package is chromium-browser.
chromium-bsu is a game.
No need to add or enable anything. It's readily available within Ubuntu's repository system, as is.

A note on chromium would be that chromium is a open-source software package, meaning it contains no closed-source software.
As oppose to the Google Chrome package, which is built on chromium, but contains non-free software like flash.

And while you can add some of the closed source things from google chrome to chromium,
You cannot add all of them.
(As an a example: while you can run Google Chrome's flash in chromium, you cannot run Google Chrome's widevine plugin in chromium.
widevine is needed watch Netflix and Amazon videos on Google Chrome, amongst other sites)

Google Chrome can only be downloaded from google.
As it is not in the Ubuntu repository system.

Edit: Looking around it seems the package for powerpc is chromium-browser-l10n
from here:
[http://packages.ubuntu.com/search?arch=powerpc&keywords=chromium-browser](http://packages.ubuntu.com/search?arch=powerpc&keywords=chromium-browser)

---

