---
title: "How do I check my video driver?"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by bsmith1051 on 2008-08-07
I've been having lots of trouble with nvidia video drivers ever since I upgraded from 7.10 to 8.04.1.  The default driver works best though it runs super-slow, e.g. the screensaver crawls.  I used to use the Ubuntu-provided "proprietary" drivers and they worked great ... on 7.10.  Now they fail to recognize my Nvidia 6100 integrated graphics.  I tried using the official Nvidia driver but I think that caused ALL KINDS of weird problems, from DVD-Rs not mounting to Fast User Switcher resetting my login (thus crashing all my programs).

I know I can root through the config files but is there a GUI to check what video driver is installed and/or which video card the system thinks I have?

---

### Post by rainwalker on 2008-08-07
You can see what graphics card you have by running ```
lspci | grep VGA
```

---

### Post by bsmith1051 on 2008-08-08
thanks!  But there isn't a GUI, something like Device Manager in Windows?  Wasn't there something like that back in 7.10?

---

### Post by phidia on 2008-08-08
Actually he knows what card he has > Nvidia 6100 integrated graphics I don't have a Hardy install right now but I guess they removed the hardware viewer. 

There have been changes with hardy's xorg too. There is the Ubuntu wiki [here]("https://help.ubuntu.com/community/Video") which hopefully will help.

---

### Post by philinux on 2008-08-08
Just install nvidia-settings from synaptic.

It turns up in System>admin

When you click it the first page tells you the driver version in use.

---

### Post by bsmith1051 on 2008-08-08
> **philinux said:**
> Just install nvidia-settings from synaptic.
Thanks, I tried it just now but it says I'm not running the Nvidia driver.  As I said in the OP I'm running the generic driver.  I finally resorted to looking through the xorg.conf file and saw that I'm running the 'nv' driver and that my card is recognized as "Nvidia 6100"

---

### Post by hansdown on 2008-08-09
Hi bsmith1051. There are a number of threads that suggest that the screensavers "may" tax your cpu. This may not be the case in your situation. I've found a few threads...  [http://ge.ubuntuforums.com/showthread.php?t=799941](http://ge.ubuntuforums.com/showthread.php?t=799941)

[http://ge.ubuntuforums.com/showthread.php?t=808652](http://ge.ubuntuforums.com/showthread.php?t=808652)

[http://mg.pov.lt/blog/ubuntu-screensaver.html](http://mg.pov.lt/blog/ubuntu-screensaver.html)

[http://www.frsirt.com/english/advisories/2007/3616](http://www.frsirt.com/english/advisories/2007/3616)

[http://answers.yahoo.com/question/index?qid=20080619133226AAE3svX](http://answers.yahoo.com/question/index?qid=20080619133226AAE3svX)

You can get a good google search by copying and pasting the title from your post into the google search bar. Hope this helps.

---

### Post by bsmith1051 on 2008-08-09
I'm not too worried about the CPU load.  Instead it's just that I can tell that none of the 3D acceleration of my card is being used (because the 3D screensaver crawls).

I've found a bunch of threads talking about problems with the Ubuntu-provided 'proprietary' drivers after the Hardy upgrade.  The solutions all sound too complicated for me to have tried, though.

---

