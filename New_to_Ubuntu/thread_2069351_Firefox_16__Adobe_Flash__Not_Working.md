---
title: "Firefox 16 / Adobe Flash / Not Working"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by S2UIRR3L on 2012-10-10
This is probably a really easy fix, but I'm just not that good yet...

First off, I'm using Lucid Lynx (Kernel Linux 2.6.32-43-generic) and
if there's anything else that would help, I'll be happy to provide it.

Update manager popped up last night and advised me that it's time
to update from Firefox 15 to Firefox 16. It's usually very painless, but
now I can't see anything that requires Adobe Flash (YouTube Videos).

I went to Adobe's site to download the latest version, this is what I got:
> **NOTE**: Adobe Flash Player 11.2 will be the last version  to target Linux as a supported platform. Adobe will continue to provide  security backports to Flash Player 11.2 for Linux.There were a few choices to download, and I don't know which one
I need and/or how to install the "missing plugins" required on YouTube.
Here's a photo of the page that I am talking about, there's info on it.

The choices are:
YUM for Linux (YUM)
.tar.gz for other Linux
.rpm for other Linux
APT for Ubuntu 10.04+

I'm "guessing" that I need either the targz or the apt,
but I don't know how to install (clueless look on face).

---

### Post by pqwoerituytrueiwoq on 2012-10-10
I am guessing you installed flash via flashplugin-installer right?
if so 
```
sudo apt-get purge  flashplugin-installer
sudo apt-get install flashplugin-installer
```
during the update process the installer fails to download flash i had it happen on 2 install of 12.10

---

### Post by S2UIRR3L on 2012-10-10
**[SIZE=4]SOLVED[/SIZE]**

Okay - I went back to the page and by accident, I hit the APT button and went with it. It opened another dialog that asked my permission to enable thrid party software installs. It automatically installed everything I needed without having to touch the terminal.

Don't I feel like a horse's @ss :P

---

### Post by Lyfang on 2012-10-10
Flash Player beyond 11.2 is available through Pepper Flash with Google Chrome or use Chromium. [Re: Chromium Flash Pepper on precise, how?]("http://ubuntuforums.org/showthread.php?t=1976503&page=2")

---

