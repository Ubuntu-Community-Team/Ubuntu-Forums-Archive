---
title: "DELL 1545 lappo will not find wireless signal.."
date: 2013-12-18
forum: New to Ubuntu
---

### Post by bernardbcollins on 2013-12-18
i'm a pretty useless 62 year old so be gentle.  

Being sick of the bill gates casino i've created a live usb of ubuntu 12.04 LTS and stuck it on the dell inspiron 1545.  No wireless signal being picked up, but i know its there and the bt hub is functional because i can use this old acer to surf.  i've searched around a bit, and tried a few things involving terminal and writing instructions but to no avail.

It would be excellent if you boffin types could help?

Thankyou:D

---

### Post by philinux on 2013-12-18
I would connect the laptop wired to the router. and use software updater to first make sure os is up to date.

Then under the gear top right choose System Settings > software and updates > additional drivers. See if the os offers to install wireless driver.

---

### Post by bernardbcollins on 2013-12-18
Tried that philinux, but the dell won't pick up the wired internet.  When i click the signal icon it appears to search for a service, but then a load of incomprehisibles pop up asking for "VPN connections", wired connection "you are now off line" (never been on!).  Filled in some password and BTHub details but no luck i'm afraid.

---

### Post by philinux on 2013-12-18
> **bernardbcollins said:**
> but i know its there and the bt hub is functional because i can use this old acer to surf. 


I took that to mean you could connect to net directly, hard  wired connection to router.

Now I'm confused.

---

### Post by bernardbcollins on 2013-12-18
Sorry, yes, i plugged the cable from the bt hub3 into the dell.  but no result.

---

### Post by bernardbcollins on 2013-12-18
The bt hub is usually hard wired to a foxsat thing, so i unplugged the foxsat end and transferred it to dell laptop. Thus, i can verify that there is an internet signal, cos it allows the foxsat and this acer to function.

---

### Post by philinux on 2013-12-18
> **bernardbcollins said:**
> The bt hub is usually hard wired to a foxsat thing, so i unplugged the foxsat end and transferred it to dell laptop. Thus, i can verify that there is an internet signal, cos it allows the foxsat and this acer to function.

So with an rj45 cable from router to acer you are accessing the internet ok?

(wired to router means cable from router to device)

---

### Post by bernardbcollins on 2013-12-18
No, the acer is wireless, and works well.

The rj45 cable (if thats what it is), usually feeds the foxsat hdr television box and enables internet access to bbc iplayer etc.

At the moment it is "wired to the router" and the dell

---

### Post by philinux on 2013-12-18
> **bernardbcollins said:**
> No, the acer is wireless, and works well.

The rj45 cable (if thats what it is), usually feeds the foxsat hdr television box and enables internet access to bbc iplayer etc.

At the moment it is "wired to the router" and the dell


Ah righto. So dell does not see net wired. Gotcha. and foxsat sees the  net ok wired?

---

### Post by bernardbcollins on 2013-12-18
correct, sorry to create confusion.  Shall i format dell and reinstall ubuntu with it hard wired to router?

---

### Post by philinux on 2013-12-18
> **bernardbcollins said:**
> correct, sorry to create confusion.  Shall i format dell and reinstall ubuntu with it hard wired to router?

I would certainly boot the live installer on the dell wired and see if it connects to net when wired.

---

### Post by richardsdma on 2013-12-18
what kind of wireless do you have? 
i have a dell inspiron 1521 and since 2011 i follow this, and i quote:

> Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.

---

### Post by chili555 on 2013-12-19
> **bernardbcollins said:**
> i'm a pretty useless 62 year old so be gentle.  62? I vaguely remember being *only* 62! The first step is to identify your wireless card, then we'll figure out how to fix whatever is missing. Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep 0280
```That funny pipe symbol | is on the right side of my US keyboard on the same key with \.

---

