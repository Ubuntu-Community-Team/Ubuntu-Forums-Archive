---
title: "dwl 650+ wireless won't connect, M.Soft MN-120 Ethernet card UNCLAIMED (doesn't work)"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Laysan_A on 2008-09-27
Hi Y'All!

I have an Inspiron 8000 with a 1Ghz processor, 384 MB of ram, and an ATI Mobility M4 32 MB video card.

I'm having problems with the video too, but I'll wait until this is resolved to deal with that.

lshw -C network properly reports both cards (I can't post the results from terminal for obvious reasons). The ethernet card is Unclaimed, and the dwl 650+ (lspci reports it as T.I. acx 100 chipset) seems to be properly configured but doesn't receive the DHCP response from the router.

I've been over the router a million times reviewing all the settings. I removed all the potential restrictions I could find, SSID broadcast enabled, WEP (the old 650+ doesn't support WPA in Windows)disabled, MAC filtering disabled, open vs. closed authentication. 

Configuration from Network (in the System Menu) works (without connecting of course), but Manual Configuration from the taskbar does not. I can input the Name field, but the ESSID field won't accept any input.

Also, I can't find Device Manager! It's definitely not in the menu. These problems with the interface, along with the failure of ethernet to connect automatically, make me wonder if my installation isn't somehow corrupted. I've reinstalled a few times, with both 8.04.1 and 8.04 (which is loaded now). Both of my i386 desktop cds passed their respective disk integrity test. 

Oh yeah, I've also tried the process described in the forum post entitled How To: Manual Network Configuration without the need for Network Manager. No joy.

I did have the previous version of Freespire installed (reformated the partition while installing Ubuntu) and could not get the wireless to work with the acx 100 driver and had to use ndis wrapper - which worked. The ethernet card worked right away too. But from reading various posts I gather this kind of thing is not unusual even when moving from Gutsy to Hardy Ubuntu.

Any ideas?

Well, I've developed a problem with the charging system, so I'm going to have to change out the motherboard (again). Since the laptop is unavailable until I do, you can disregard this post. I'll repost (or bump and edit - whichever seems appropriate) when I get it done. It doesn't seem appropriate to mark this thread as solved, so I'm not going to. I hope that's the right thing to do in this situation...

Thanks!

---

