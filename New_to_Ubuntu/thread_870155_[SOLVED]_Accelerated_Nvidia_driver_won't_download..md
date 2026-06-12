---
title: "[SOLVED] Accelerated Nvidia driver won't download..."
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Brightbelt on 2008-07-25
Hi,
I just installed Xubuntu and am trying it for the first time after being a fairly long-time Ubuntu user.

There IS an accelerated (proprietary) driver for my Nvidia GeForce Go 7600 listed in the Hardware Drivers section. So I check to enable it and it begins to download.

But then it stops and says "We were unable to fetch...blah blah repository name/Nvidia name etc etc"

I get the same thing in the Synaptic Package Manager.

I AM able to browse (I'm here...) and my wireless is up and running. Is this just a temporary repository lockup or what could it be?

I appreciate any assistance.

Many Thanks, Frank B.

---

### Post by Titan8990 on 2008-07-25
Try using Envy to install your drivers:

sudo apt-get install envy

---

### Post by silkstone on 2008-07-25
Most likely it is a temporary glitch with the repo - it can happen. Try again in a while and see how it goes.

---

### Post by Brightbelt on 2008-07-25
Thanks for the help guys. Yes, I'm very familiar with Envy - I usually use that only when there's a compatibility problem with the graphics card.

So I used EnvyNG here and it worked fine. 

Also, just to be correct in case a beginner looks in and gets confused, the basic code 'sudo apt-get install envy' wasn't exactly right for Xubuntu 8.04 (that returned an error). The actual code that the Envy website gave was this (and it worked):

```
sudo apt-get install envyng-gtk
```

That line applies to both Xubuntu 8.04 and Ubuntu 8.04. 

Again Many Thanks and my apologies for the delay in thanking you -- it's Friday and the day got away etc...

Frank B.

---

