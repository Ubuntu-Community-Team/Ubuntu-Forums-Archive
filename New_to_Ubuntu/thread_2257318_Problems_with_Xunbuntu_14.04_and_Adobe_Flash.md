---
title: "Problems with Xunbuntu 14.04 and Adobe Flash"
date: 2014-12-18
forum: New to Ubuntu
---

### Post by wsfield99 on 2014-12-18
Hi, please forgive me if this is redundant.  I just installed Xubuntu 14.04 on a Panasonic Toughbook CF-28, Pentium 111, 1000 Mhz, with 512K ram.  I had been running Ubuntu 12.04 on this machine.  I can't get anything to work right.  Specifically, I am unable to open and videos that require Flash.  I somehow managed to install the current version of Flash in Firefox and it shows up in the add ons but does not work.  Basically I can't use Youtube or Hulu.  I tried installing the Chromium browser but if won't open.  I'm sure I will need to supply additional info.  Thanks in advance for your help.  Scott

---

### Post by JeQhdMD on 2014-12-18
Although xubuntu might run "ok" with your system specs & ram, you might have better luck with Lubuntu 14.04 . . . might even have enough ram to run chromium then.   ALso, for flash, you should go into the Lubuntu Software Centre (or whatever it's called now) and install "Lubuntu restriced-extras" (or something close to that).   If I recall right, that will pull-in all your media codecs including flash.   (there is also the restricted-extra package for Xubuntu) . . . . . you might also consider running one of the lighter browsers (midori or QupZIlla).

---

### Post by DuckHook on 2014-12-19
A Pentium 3 is a very old CPU for any modern GUI, even Lubuntu. You can try it, but with your system specs, I wouldn't count on a good experience even on Lubuntu.

If you really like monkeying around with ancient HW (I do), then these sorts of laptops are a great hobbyist's challenge to bring back to life and make useful. However, if you just want to get work done on it and are not into tinkering, then I would actually suggest a non-'buntu distro for your machine.

Try any of the following:
Puppy Linux
Tiny Core
SliTaz

Be prepared for a challenge with any distro that you choose. The components in your laptop are so old that modern kernels may not have the driver baked in for it anymore. Example: does your WIFI work?

The best use for HW as old as yours is to use them as command-line-only servers and forego the GUI altogether. They are actually quite useful if used in this way. See my comments in [this]("http://ubuntuforums.org/showthread.php?t=2128594&p=12571319#post12571319") earlier post.

Your issue with flash is due to the fact that a P3 does not support SSE2, which is needed for modern flash. There is no way to make it work without really ugly kludges, mostly having to do with installing ancient versions of flash and then preventing your OS from ever updating flash. Moreover, your video subsystem is the Intel 830MG which is not only restricted to 32MB, but must steal it from your already limited RAM. It doesn't have much hardware acceleration either, so many video functions like 3D will have to render using your already overtaxed CPU.

At the risk of repetition, a P3-based box is about the lowest CPU in which old HW can still be made useful, and it requires a lot of work to do so. If you still want to do this, then it's an involved process with no guarantee of victory, but there are probably a few of us around here who could help you along the way.

[This]("http://ubuntuforums.org/showthread.php?t=2130640") sticky is an excellent resource. mörgæs is a guru on old HW who has body-slammed more ancient equipment into submission than Hulk Hogan. He gives realistic expectations about what you will likely achieve along with detailed instructions on how to get there. If you wish to go further, then post back to this thread the results of what mörgæs asks in his sticky, especially post #1, subheading "2 Hardware".

---

### Post by wsfield99 on 2014-12-19
Thank you.  I do have wifi (oddly enough).  I was doing o.k. until I decided to try to upgrade from Ubuntu 12.04.  My wife will probably kill ( or at least maim me) if I spend anymore time fiddling with this old machine than I already have.  Thanks again, Scott

---

### Post by DuckHook on 2014-12-19
You may wish to go back to 12.04 which you know will work. There's nothing wrong with it. Xubuntu is supported until 2015 and Ubuntu is supported until 2017.

---

### Post by Yellow Pasque on 2014-12-19
Flash won't run on a Pentium 3 (it requires the CPU to support SSE2).

---

