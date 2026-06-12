---
title: "How do I get to know my &quot;unknown&quot; network connection"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by t0p on 2008-08-18
I use a cellphone as a modem to connect to the internet.  My phone (Sony Ericsson K800i)  detects the USB datacable when it's plugged in and automagically connects to the internet.

Thing is, my conky, which is supposed to display network speeds, shows them as zero.  In Network Settings, **System > Administration > Network**, everything is greyed-out.  If I right-click on the Network icon on my top panel, and select Connection Information, it tells me the following:

> Interface: Ethernet (usb0)
Speed: unknown
Driver: cdc_ether

So, can I enable the system to know connection speeds etc?

---

### Post by anaconda on 2008-08-18
I suppose your problem is that the network manager doesnt regognize your internet connection at all.

If you look at System>Administration>System monitor
and from there the resource tab. That should show the correct network speed and history.

Another annoying problem if network manager doesnt recognize your internet connection is that firefox will always start in "offline" mode

I solved that with removing NetworkManager

---

### Post by t0p on 2008-08-18
> **anaconda said:**
> 
If you look at System>Administration>System monitor
and from there the resource tab. That should show the correct network speed and history.


Thanks, I never noticed that before.

So, is there a way of getting conky to read this info from the system monitor and display it?

---

