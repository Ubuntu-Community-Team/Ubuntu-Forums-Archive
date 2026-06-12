---
title: "Is getting Ubuntu to work with a Wireless dongle really just a waste of time?"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by Peppone21 on 2013-01-27
Hi,
Are there any beginners guides to Wireless hardware or hardware configuration in general?

I'm completely new to Ubuntu and fairly new to using a command line for anything much on any platform.

I got a wireless USB dongle a few weeks ago. I spent a while trying to get it working. After about a week on the forums, I finally did so. Once I'd done that I could move the Ubuntu machine away from my router and set it up where I wanted to.

It worked fine for about a week but now it's stopped doing so.

Has anyone written a general troubleshooting guide to getting Ubuntu working with Wireless dongles or other wireless cards? I ask because a friend of mine said to me 'Ubuntu is fine for a lot of things, but you should just give up trying to get it working wirelessly" - he said that every time he gets it working, it breaks after a short while and each fix is some new time-destroying adventure.

If this is the case, I will give up on wireless and rearrange my house (not easy) but if I could find something written for idiots that would tell me what command line diagnostics to run and how to read the results, that would be great. The additional problem is that - without an internet connection on my Ubuntu machine, I have to post to forums from a PC elsewhere in the house and then print off and try suggestions on the Ubuntu machine upstairs.

Thanks

Paul Evans

---

### Post by Cheesemill on 2013-01-27
If you want the easiest answer then it's 'buy a wireless dongle that supports Linux'.

I have several machines that use wireless and they have all worked flawlessly without any tweaking needed on my part. This is because I make sure that the wireless dongles I use are supported by the Linux kernel before I buy them.

---

### Post by mcduck on 2013-01-27
Depends on the exact make and model of your dongle. In most cases things like that will work automatically and without any problems, but of course there are always some specific devices that might cause troubles.

Anyway, the best way to sort it out is to give as much information about the device as possible, and then perhaps somebody here might have an idea how to get it working.

---

### Post by Cheesehead on 2013-01-27
If you had it working, but then it stopped, then look for changes you made around the time it stopped.

Perhaps you upgraded the kernel and didn't re-install the dongle's kernel module. Perhaps you installed a conflicting udev rule telling the system to ignore the dongle. Perhaps you were 'cleaning up' and uninstalled something essential.

There are many 'Beginner Guide to Networking' guides floating around. Here in the forums is at least one great sticky on the subject. [http://help.ubuntu.com](http://help.ubuntu.com) has many good beginner-guide pages.

The issue you describe, however, does not seem beginner-level. Nor common enough to go into one of those guides.

You could show us the [FONT="Courier New"]lsusb -v[/FONT]  hardware readout on the dongle.
And a link to the instructions you used to successfully get it working the first time.

---

### Post by terabyte1 on 2013-01-27
Hi! Not a waste of time - if you know what dongleyou want. You should try to match your dongle with the type of wi-fi you get from your isp, such as b/w/ or N type of wifi you get, then, type in your username for your wifi and your password for it - infor is found on your router - once set it should work.Hope that helps! Good Luck and happy Ubuntu-ing:guitar: terabyte1

---

### Post by sanderj on 2013-01-27
If it doesn't work automagically, and certainly if you don't like the command prompt, then, Yes, it's probably a waste of time.
As someone else says in this thread: best to only use hardware that works automagically under Linux. 

So buy a USB wifi dongle that works immediately after plugging it in.
As a rule of thumb: first find out if it works on Linux, then buy. Not the other way round. Certain manufacturers are good with Linux (Intel and Realtek for example), others are not (Nvidia, AMD/ATI, Atheros).


Out of curiosity: "wireless USB dongle" ... hasn't your system Wifi built-in? Oh, is it a desktop?

---

### Post by coldraven on 2013-01-27
Maybe your trouble is interference from other wifi or cordless phones. You can change the channel in your router and see if it makes a difference. 
I've been using Ubuntu with wifi for years and not had any problems.

---

### Post by terabyte1 on 2013-01-27
Pepone - we were all once beginners, I came in using Dapper Drake - so long ago now! I use the cloud and its really cool to put important files on you don't want to lose - you've got 5gb I think bu you can buy more and its really  cheap with Ubuntu - cheaper than the others! There are many beginers guides - if you look for them! They are kool especially for old  guys like me sho forget things more easily these days :p Have Fun with Ubuntu!:D

---

### Post by kurt18947 on 2013-01-27
> **Cheesemill said:**
> If you want the easiest answer then it's 'buy a wireless dongle that supports Linux'.

I have several machines that use wireless and they have all worked flawlessly without any tweaking needed on my part. This is because I make sure that the wireless dongles I use are supported by the Linux kernel before I buy them.

Best answer!  Other devices can range from annoying - such some Realtek chipsets that are not yet supported natively but the manufacturer has drivers for download with install scripts - to borderline impossible - adapters that have NO linux support and Windows drivers in .exe format only so NDISwrapper is difficult.

---

### Post by DuckHook on 2013-01-27
I have several old laptops with the infamous broadcom chipsets and these are wired in--not even a dongle that can be replaced--so I feel your pain. Every time I install a new system (I like clean installs--not upgrades), I must go through the involved process of downloading the legacy driver modules, extracting the firmware, building the driver, blacklisting competing drivers and installing the right one. It's irritating for someone like me, and obscure and downright intimidating for new users, so I wish it could be different. The trouble is: it can't. Here's why:

In Linux, most drivers are compiled into the kernel. This is what makes the OS so portable. You can install Linux on a USB stick and chances are that it will boot up on most modern hardware with no fuss. Try doing that with Windows. No way. And we won't even get into MacOS. The slightest hardware difference from the installation state will send Windows into a panic. If you change the number of processors on it, it won't even boot. In this sense, Linux is actually the easier OS to use, because it is hardware independent.

However, this functionality comes at a cost. The maintainers can't just leave every driver module in the kernel because the kernel would grow to GBs in size. So they prune aggressively, which leaves a lot of older equipment out in the cold. New equipment poses a different problem because their proprietary drivers are opaque so their functionality has to be reversed engineered. This takes time and effort and, if the device is not at least somewhat in demand, may never even be done. After all, it is a community contribution effort. The saving grace is that modules can still be installed if you know what you are doing.

This is what I've found:

1. The easy way is to only buy equipment that has been proven to work with Linux.
2. However, this is not always practical. In my case, it's the legacy equipment that I already own.
3. So, if you have the time and the inclination, the best way is to tinker with it. Can't tell you how much I've learned about this amazing/frustrating OS through the dogged process of trying to make something work. Make no mistake: it will be challenging, so know what you are getting into if you choose this last route.

So to answer your question: no--if you are inclined towards the geeky side, getting it to work is not a waste of time.

---

