---
title: "ndisgtk wireless doesn't work"
date: 2012-12-14
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-12-14
How do I usendisgtk to load a wireless driver

I've installed Lubuntu 12.04 
Compaq CQ57-410TU XC7973 Presario notebook 802.11 b / g / n
I think mine is RTL8188CE but I'm not sure.
I've been trying for days on all the forums to solve this.

Any help would be appreciated.

---

### Post by verymadpip on 2012-12-14
First identify your wireless card:

Open a terminal & run:

```
 lspci
```The line from my box looks like this:

```
04:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
```You're looking for the "Network Controller" probably.  Once you have that information you need Windows XP (more than likely) drivers, but let's go one step at a time for now.

I've had problems with ndiswrapper from Software Centre (& Synaptic) so I've been installing from a tarball form Source forge.  We can get to that later if necessary.  You should check that it's installed properly.  Open a terminal & run:

```
ndiswrapper -v
```
Post the results from this & lspci in a reply please bud, preferably between code (#) tags

I'm out for a few hours, so I'll check back later.

---

### Post by squakie on 2012-12-14
verymadpip is giving you good advice:  you (and us) can't "guess" at a chipset - that would be a bad thing.  So, please do post back the output of lspci as they requested.

If it is the rtl8188ce:

*If* you end up needing ndiswrapper, verymadpip mentioned something I'd like to expand on as it is very important:  unless something has changed since the last time I used it, ndiswrapper requires 2 things of the driver files:

- must be from Windows XP

- must match the architecture of your Ubuntu install 32-bit for 32-bit Ubuntu, 64-bit from 64-bit Ubuntu


I might be wrong here, so I need to do some more looking first, but I think that chipset can be made to work without ndiswrapper.  I'll do some checking and see if I find anything.

In the meantime, try a search in the forum with:

12.04 rtl8188ce

Also try a net search with:

ubuntu 12.04 rtl8188ce

or

linux rtl8188ce

---

### Post by verymadpip on 2012-12-14
Hi again.
I don't wish to complicate matters, just need to add that I did find an exception to the XP drivers rule (of course it would be me - anything to make things a little less smooth).  Definitely an exception though.

I also didn't know ndiswrapper would work with 64 bit architecture - always good to learn these things .

---

### Post by squakie on 2012-12-14
> **verymadpip said:**
> Hi again.
I don't wish to complicate matters, just need to add that I did find an exception to the XP drivers rule (of course it would be me - anything to make things a little less smooth).  Definitely an exception though.

I also didn't know ndiswrapper would work with 64 bit architecture - always good to learn these things .

I can't say I've ever used ndiswrapper with 64-bit ubuntu either - I just seem to remember reading that somewhere and have been passing it along - maybe I shouldn't be!  Heck, was there even a 64-bit Windows XP?

Thanks for the info!  ;)

---

### Post by verymadpip on 2012-12-15
It appears that there is a x64 bit version of XP Professional.  I think other 64 bit versions are for Itanium CPUs.  That looks like a whole other ball game to me though.

I use ndiswrapper with a Netgear WPN11 on 32 bit Xubuntu, it works a treat.

---

### Post by squakie on 2012-12-15
> **verymadpip said:**
> It appears that there is a x64 bit version of XP Professional.  I think other 64 bit versions are for Itanium CPUs.  That looks like a whole other ball game to me though.

I use ndiswrapper with a Netgear WPN11 on 32 bit Xubuntu, it works a treat.

In the past I always seemed to get PC's and adapters that had the ubiquitous Broadcom chipsets and in those days you had to use ndiswrapper.  I found it pretty easy to use and it always worked well for me.  Adding the use of ndisgtk just made things that much easier.   I would say I long for those days ;) however it does seem easier now.  I just don't like that there are so many old threads out there that can be found via the net that are way outdated now, so a lot of new users try to help themselves and then find that for their wireless they shouldn't have tried ndiswrapper.

---

### Post by Kevin McCready on 2012-12-16
Thanks for all these suggestions. 

I managed to get the wifi going, BUT only as a temporary USB boot with tinycore linux. They have a brilliant wifi app on the home screen. You just click on it and the app lists all the available wifi's, you click on yours and put in the password and bingo.

Is there any app in our repositories which will do that from the command line?

Maybe it's something wrong with our kernel? The one i used from tinycore was:
CorePlus-4.7.1.iso

---

### Post by squakie on 2012-12-16
Uh, click on the network manager icon - any available networks show there.

Please post back the lspci as request -  we do need to know the chipset the adapter is using in order to help you.

---

### Post by verymadpip on 2012-12-16
H'mmm, yeah, what squakie said.  I've found the native network manager to be quite reliable.

---

### Post by Kevin McCready on 2012-12-16
I had already done that. No wifi shows. Is there another app that does the same as the tinycore linux app?

---

### Post by verymadpip on 2012-12-16
> **squakie said:**
> Uh, click on the network manager icon - any available networks show there.

Please post back the lspci as request -  we do need to know the chipset the adapter is using in order to help you.

You do have networking & wireless enabled in the network manager dropdown menu don't you?

---

### Post by Eugene King on 2012-12-16
I loaded Lubuntu on a USB to use at work and bought a Netgear WiFi adapter that has the same realtek chip set and ended up going back to Ubuntu 11.10 where the adapter works flawlessly. 

It will be nice to see how this pans out............

But what I really would like is to get my iPhone 5 to USB teather like my old 3GS iPhone did. I dislike that it broadcasts my link.

---

### Post by kurt18947 on 2012-12-16
If you do indeed have a realtek adapter, you might check realtek's site.  I have a few realtek adapters.  8192SU is just plug -n- play.  There is an easily fixed suspend/resume issue with that chip set. 8188CUs is recognized in modern distros but doesn't work well.  I download the driver from Realtek's site, run the install script and ta-da, it works reliably. Sometimes I had to blacklist the 'native driver' sometimes not. The point being RealTek does offer native linux drivers for many of its chipsets.  You do have to know which one you have though.  "lspci" or "lsusb" in a terminal should give you something along these lines:

```

Bus 003 Device 002: ID 07d1:3303 D-Link System DWA-131 802.11n Wireless N Nano Adapter(rev.A1) [**Realtek RTL8192SU**]

```

---

### Post by squakie on 2012-12-16
> **kurt18947 said:**
> If you do indeed have a realtek adapter, you might check realtek's site.  I have a few realtek adapters.  8192SU is just plug -n- play.  There is an easily fixed suspend/resume issue with that chip set. 8188CUs is recognized in modern distros but doesn't work well.  I download the driver from Realtek's site, run the install script and ta-da, it works reliably. Sometimes I had to blacklist the 'native driver' sometimes not. The point being RealTek does offer native linux drivers for many of its chipsets.  You do have to know which one you have though.  "lspci" or "lsusb" in a terminal should give you something along these lines:

```

Bus 003 Device 002: ID 07d1:3303 D-Link System DWA-131 802.11n Wireless N Nano Adapter(rev.A1) [**Realtek RTL8192SU**]

```

Kevin - several of us have requested you give us that output in our prior posts.  We NEED that in order to help you.  Otherwise we could give you all kinds of advise but it may not apply and could make things harder to "undo" before trying to make it right.

PLEASE post back the output so we can help you!

---

### Post by verymadpip on 2012-12-17
> **Kevin McCready said:**
>  Is there another app that does the same as the tinycore linux app?

Well, I suppose there's wicd.  I don't think it coexists with Network Manager very well though.  That could get messy.
This may help:

[http://ubuntuforums.org/showthread.php?t=2001290&highlight=wicd+network+manager+conflict](http://ubuntuforums.org/showthread.php?t=2001290&highlight=wicd+network+manager+conflict)

lspci & lsusb would still help.

---

### Post by Kevin McCready on 2012-12-17
Thanks so much for your help. Please have patience with me (I'm spending all of my days in hospital with my mum in law who's just had a stroke).

I installed wicd which now recognises the wireless. But I am not sure whether to tick the static or IP or static DNS, or either, or how to configure it. When I put in the network name and password, wicd tells me it's a bad password, even though it isn't. 

Here's the output of lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)

Here's the output of lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 05c8:021e Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 003: ID 0458:0037 KYE Systems Corp. (Mouse Systems)

I'm not sure these outputs are needed now that wicd see the modem. When I get home tonight I'll try to check the other link about the conflict issue.

Thanks again so much.

---

### Post by verymadpip on 2012-12-18
Uh, I was going to say I've got an ancient tablet that I use wicd on, I'll check my settings. Then I remembered wicd irritated me for some reason so I removed it - sorry about that.

I've never used a static anything for my wireless connections on a number of rigs & various OSs.
Really we need one of our wireless whizzkids to help here.  It's out of my scope I'm afraid.

Perhaps this will help:
[http://www.upubuntu.com/2011/07/install-wicd-to-configure-and-connect.html](http://www.upubuntu.com/2011/07/install-wicd-to-configure-and-connect.html)

---

