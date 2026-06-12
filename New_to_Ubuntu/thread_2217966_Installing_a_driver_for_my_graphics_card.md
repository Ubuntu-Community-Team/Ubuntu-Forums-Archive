---
title: "Installing a driver for my graphics card"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by sanssadness on 2014-04-19
I am running Ubuntu 12.04 LTS. I have been trying to find out how to install the open source RadeonDriver described here (I suspect it isn't installed because in programs where I use the scrollbar, I feel some lagginess, so I'm guessing only a default video driver is used):

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I ran into a few problems/questions:

1. Did Ubuntu already install this driver when I installed Ubuntu itself? How can I tell what driver is currently being used?

2. Assuming I don't have the RadeonDriver installed, is it supported? My card is listed in that large list in the middle, but at the bottom of the large list it says "Requires Ubuntu >= 12.10 or updated package". Does this mean 12.04's not good enough or can I still install the "updated package"?

3. Any other suggestions or comments would be appreciated!

---

### Post by 3rdalbum on 2014-04-19
The Radeon driver is already installed. The "lagginess" when using the scrollbar might be simply that Ubuntu does not smooth out the action of scrolling like Windows XP does - this is normal. If the lagginess is something different, or very slow, it might be that your card is not supported very well by the open-source driver.

If your graphics card is supported by the AMD proprietary driver (fglrx) you should install it, because it will undoubtedly give you better performance.

What card is it?

---

### Post by sanssadness on 2014-04-19
My video card is the ATI Mobility Radeon HD 3470, which is on the main list on the RadeonDriver wiki page. It is a "mobility" card probably because this is a laptop. What is Ubuntu 12.04's behavior when dealing with video cards? Is it like Windows, where it has a default (very basic) driver that can only display the lowest resolutions and give users enough visibility to install a better driver? Does it install the open source RadeonDriver right away for AMD cards (and is this driver the basic one)? It isn't just the scrolling that bothers me. When I drag icons from the dash to the desktop, I also notice some lag. One more thing: I wasn't connected to the Internet when I installed Ubuntu. I don't know if this affected the installation of the driver.

In the end, I might choose to install the fglrx driver, but I still need a way to test which driver is currently installed in case I have problems with it and need to go back to the open source driver (or some other driver). Is there some kind of utility or command I can use to test what driver I have installed at the moment?

---

### Post by 3rdalbum on 2014-04-19
DO NOT install fglrx, your card is not supported by it. (only RadeonHD 5000 and above)

You are already using the open-source Radeon driver, that is the only driver for your card therefore it is already in use.

There should be some HOWTOs around for turning off semitransparency and animations in Unity, that may improve performance considering that the Radeon driver only has a small amount of 3D acceleration capability.

---

### Post by monkeybrain20122 on 2014-04-19
fglrx will not work on your card and installing it will kill your display for sure. But the open driver from 12.04 is old and outdated even for the point releases. You may get better performance by updating the open driver with this ppa [https://launchpad.net/~pali/+archive/graphics-drivers](https://launchpad.net/~pali/+archive/graphics-drivers)

But updating graphic driver always carries some risks so you should ponder whether it is worth it. If you decide to update don't forget to install ppa-purge in case it breaks something. Disable the ppa after updating (so you won't get further updates that may break)

---

### Post by trag on 2014-04-19
try this graphics install procedure, wiki will provide further info regarding current and legacy drivers. [http://sourceforge.net/projects/uaci/?source=directory](http://sourceforge.net/projects/uaci/?source=directory)
good luck 
trag

---

### Post by deadflowr on 2014-04-19
> 2. Assuming I don't have the RadeonDriver installed, is it supported? My  card is listed in that large list in the middle, but at the bottom of  the large list it says "Requires Ubuntu >= 12.10 or updated package".  Does this mean 12.04's not good enough or can I still install the  "updated package"?

If this is a very recent install of 12.04, then I might assume it is the one with the saucy kernel.
In which case, you would be using the > than 12.04 updated package.
Meaning you have the saucy X stack, as per [LTS hardware stack enablement]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")
This is a guess, though. As I don't know what you installed.
A quick
```
uname -a
```
should tell which kernel you have, and from that we can get a basic idea.
3.2 = precise
3.5 = quantal
3.8 = raring
3.11 = saucy
and the final point release later this year will move all the non precise stacks up to trusty's.
3.13
Based on the kernel, you should have the correlated X stack, unless you install something.
(You would know if you install something for X)
But as it is, you probably aren't going to be able to do much with your card, anyway.
My opine, though.

---

### Post by sanssadness on 2014-04-20
Well it's an old computer, and I'm not exactly planning to do the latest  in graphics stuff with it, but it would be nice to be able to use it to  its limit (or close to its limit), maybe to play some old games.

uname -a gave a bunch of gibberish along with this: 3.8.0-38-generic

I think this might be the kernel version.

So should I go for the ppa or what? The wiki page I posted isn't very helpful regarding what driver comes with my 12.04 version.

By the way, how can there be different kernel versions for 12.04? I thought everyone used the same install CD.

---

### Post by deadflowr on 2014-04-20
> By the way, how can there be different kernel versions for 12.04? I thought everyone used the same install CD. 				

The link I gave explains it pretty well.

When Ubuntu LTS hits the point release, then the version from Ubuntu.com becomes that version.
Basically, everything about the release is the same, expect the kernel version and graphics stack.

They do this because 12.04 has a longer support period, thus hardware for newer system would have problems running on software that is not built to run it.
By continually upgrading the hardware stack you increase the chances that the newer system will run it.

Hope that makes sense.

---

### Post by sanssadness on 2014-04-20
From my limited knowledge of Linux, it seems to me these are "invisible" newer releases of 12.04. The general public thinks 12.04 is all one version, but the kernel is in fact updated even within a release. Does that sound about right?

By the way, you have my kernel version now right? I'm looking at all these different posts, and I'm trying to decide what to do about my graphics driver. Do I just stay put, add a ppa, upgrade to 14.04, or what?

---

