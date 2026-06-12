---
title: "Whats going on with the b43 driver?"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by OhioYJ on 2008-07-25
Ok so my BCM4306 card has worked perfectly in 6.10, 7.04, 7.10, and even used to work in 8.04, now it doesn't work. After spending days trying to get it to work, and even stumping some experts here, I gave up and installed Windows temporarily (this one notebook has to work, first time Windows has been on it in 2 years now....). Tonight while searching for a new distro, thinking this was limited to Ubuntu, I find this has become quite an issue for many people who have the BCM4306 card in other distros too? 

My programming skills are quite basic, so I don't have the ability fix the driver, but it makes me wonder if the developers of the b43 driver are aware of the issue? I've checked their site over, and I don't see any way to contact them, or a forum dedicated to it. Suggestions?

---

### Post by mal_conductor on 2008-07-25
OhioYJ,

Can you tell me how to install in prior versions?

I'd like to try what you are doing to see if I get similar results.

---

### Post by OhioYJ on 2008-07-26
In prior versions, all I do is install bcm43xx-fwcutter, type in sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o, and it works without issue.

I have the bcm43xxfw-cutter.deb file downloaded, and the wl_apsta.o, perhaps they are older files, but they work for me? They do not work in 8.04 though. I even tried disabling the B43 driver, no luck. 

If there is more information I can give about something that would help, I'm more than happy to temporarily install it again. I don't have the ability to fix the problem, but I'm willing to do anything I can to help those that can fix the problem.

---

### Post by falcon61102 on 2008-07-26
Have you tried downloading the latest WinXP driver to use along with the lastest version of b43fwcutter?

---

### Post by Tim Sharitt on 2008-07-26
The b43 driver in 8.04 is not the same as the bcm43xx driver in previous versions. The b43-fwcutter package is used to install the firmware for this driver.

---

### Post by Tim Sharitt on 2008-07-26
> **OhioYJ said:**
> In prior versions, all I do is install bcm43xx-fwcutter, type in sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o, and it works without issue.

I have the bcm43xxfw-cutter.deb file downloaded, and the wl_apsta.o, perhaps they are older files, but they work for me? They do not work in 8.04 though. I even tried disabling the B43 driver, no luck. 

If there is more information I can give about something that would help, I'm more than happy to temporarily install it again. I don't have the ability to fix the problem, but I'm willing to do anything I can to help those that can fix the problem.


Disabling the b43 driver had you half way there, but you must also enable the bcm43xx driver.

---

### Post by OhioYJ on 2008-07-26
> The b43-fwcutter package is used to install the firmware for this driver.

While using the b43 package, I used b43-fwcutter driver. It then created the b43 folder, and b43_legacy folder in the firmware directory. According to the b43 site, my particular card (rev 3) must use b43_legacy, but Ubuntu says its using b43.

> Disabling the b43 driver had you half way there, but you must also enable the bcm43xx driver.

Maybe this is the key. When I blacklisted the b43 driver, I removed the bcm43xx driver from the blacklist file. Is there maybe something more I should be doing?

Thanks for your guys help so far, maybe I might get it back to a working state yet?

---

### Post by OhioYJ on 2008-07-26
> Have you tried downloading the latest WinXP driver to use along with the lastest version of b43fwcutter?

I've tried letting it download the file, and using the wl_apsta.o file I've always used in the past, neither work. I tried the actual driver from Compaq, but I had tried to use the bcml5.sys file (I know that file name isn't correct). No luck with those?

---

### Post by falcon61102 on 2008-07-26
I'm not the most familiar with b43fwcutter, but have you tried to use ndiswrapper?

---

### Post by Tim Sharitt on 2008-07-26
In a terminal try
```
sudo rmmod b43
sudo modprobe bcm43xx
```

---

### Post by OhioYJ on 2008-07-27
> but have you tried to use ndiswrapper?

I've never got ndiswrapper to work for this particular card.

---

### Post by OhioYJ on 2008-07-27
> In a terminal try

Yeah I don't think I've tried that. I'll install Ubuntu and give that whirl when I get home. I'll keep my fingers crossed.

---

### Post by falcon61102 on 2008-07-27
In saying that you never got it to work, I'm guessing that you tried it.  If you haven't completely removed ndiswrapper after trying it and it not working, that may be causing you some problems in that it may be trying to load a bad driver.  

If you did try it, did you completely remove it before trying something else?

---

### Post by Tim Sharitt on 2008-07-27
> **falcon61102 said:**
> In saying that you never got it to work, I'm guessing that you tried it.  If you haven't completely removed ndiswrapper after trying it and it not working, that may be causing you some problems in that it may be trying to load a bad driver.  

If you did try it, did you completely remove it before trying something else?

Yes, if ndiswrapper is still loaded it will prevent the other drivers from working (and ndiswrapper won't work if b43 or bcm43xx is loaded).

---

### Post by falcon61102 on 2008-07-27
Yeah, what I was worried about is that he may have tried a couple different things (ndiswrapper/b43fwcutter) and now they are fighting for control of his wireless adapter and he's not going to get anywhere without disabling/removing one of them before trying anything else.

---

### Post by mal_conductor on 2008-07-28
OhioYJ,

I have the same card as you.  My card is now working great.

This is what I did:
(I suggest you do a fresh install.  I was following all kind of advise and nothing seem to work.  I think all this fooling around messed something up so that new attempts would not install the card)

Credits to Ayuthia.

1) Fresh install
2) get connected on a wire
3) Enable the Universe repository
- System/Administration/Software Source
- Uncheck and Check again "Community-maintained Open Source Software"
- Close
- Reload
4) Enable Wireless Driver
- System/Administration/Hardware Drivers
- Check "Enable"
- Click "Enable"
- Check "Fetch and extract firmware?"
- Click "Forward"
- Reboot

This takes less than 10 minutes.  Works great.  You may need to reboot a few times.

---

### Post by RequinB4 on 2008-07-28
firmware cutter gives you much worse preformance than ndiswrapper.

Have a look: [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by OhioYJ on 2008-07-28
Thanks to everyone for your continued support, I'm getting ready to try and install Ubuntu again right now to try a couple of the new ideas that have appeared.

> I have the same card as you. My card is now working great.

Is your rev 3? I went through several fresh installs trying different things. Even just letting it do the firmware it does not work in 8.04. I don't know why my computer is being so difficult about this. 

I do know this is limited to B43 and Ubuntu, I'm typing this from my laptop, wirelessly, running the latest version of Debian. 

I don't want to let this thing beat me though, I'm getting ready to install Ubuntu 8.04 right now, then try this:

> sudo rmmod b43
sudo modprobe bcm43xx

Then use bcm43xx-fwcutter like I have in the past.

---

### Post by mal_conductor on 2008-07-28
Try the steps I posted.
No messing, Ubuntu does it all.  It cuts the Firmware from a driver for you.  The steps I posted are all you need.

This is my info:  Yes Ver 3

description: Network controller
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 2
bus info: pci@0000:02:02.0
version: 03
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=32 module=ssb

---

### Post by OhioYJ on 2008-07-28
Ok I started off with just letting Ubuntu fetch, and install the firmware. No go, even after a restart.

Then I started with disabling the b43 driver to move to the bcm43xx. Inlcuding this step from Tim Sharitt:

sudo rmmod b43
sudo modprobe bcm43xx

Still no luck. So then I tried all the steps in order from RequinB4's link above. No luck on the Ndiswrapper though it always says alternative driver present, bcm43xx.

So I re-install Debian and am typing this over the wireless connection right now. I guess I'm just overlooking something in Ubuntu. First time it hasn't worked in Ubuntu before.

---

