---
title: "veeeery slow network w/ 8.04"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by bedfordd on 2008-04-28
I re-installed over 7.10 and all was good until I went to my network. I was able to use an internal wireless card but didn't no luck w/ 8.04 so I plugged in my USB wireless and it started right up! Now, however it is insanely slow. Even looking up a DNS can timeout. I can get as much as 40kb/s but usually it is below 10kb/s, obviously this is a non-starter. When looking at the network properties I see the wireless speed at 2M - much slower than I'd expect but I thought it would still be faster than this!

Any ideas on where to start?

---

### Post by artir on 2008-04-28
Name of your USB wireless card?

---

### Post by phidia on 2008-04-28
What internal wirleless card do you have? You maybe want to get that working with Hardy.

Check the stickies at the [wireless section]("http://ubuntuforums.org/forumdisplay.php?f=336") and you can also search either of your wireless devices there. Hope that helps.

---

### Post by Cresho on 2008-04-28
> **bedfordd said:**
> I re-installed over 7.10 and all was good until I went to my network. I was able to use an internal wireless card but didn't no luck w/ 8.04 so I plugged in my USB wireless and it started right up! Now, however it is insanely slow. Even looking up a DNS can timeout. I can get as much as 40kb/s but usually it is below 10kb/s, obviously this is a non-starter. When looking at the network properties I see the wireless speed at 2M - much slower than I'd expect but I thought it would still be faster than this!

Any ideas on where to start?

your usb is 1.0!  you really should tell us how old your hardware is instead of my guessing your problem.  You are better off with a supported pcmcia card.  I know this for a fact because I had the same issue with my HP armada 1750 (80gb hardrive p2 300mhz with 256mb memory)

---

### Post by bedfordd on 2008-04-28
Will do. I'll dig into the box tonight and get back the internal card info. I know the USB is a Linksys WUSB54G. Thanks all for the help!

---

### Post by bedfordd on 2008-04-29
Okay, the internal is a Netgear WG311v3 802.11g Wireless PCI. I was able to get it working on Feisty via: [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3?highlight=%28WifiDocs%2FDevice%29)

Also, (no idea if related) when I sudo, I get "sudo: unable to resolve host ubuntu-desktop" (and yes, hostname=ubuntu-desktop). This just started yesterday.

Thanks for any suggestions.

---

### Post by bedfordd on 2008-05-01
I found a good work-around at post: [http://ubuntuforums.org/showthread.php?t=768301](http://ubuntuforums.org/showthread.php?t=768301)

---

