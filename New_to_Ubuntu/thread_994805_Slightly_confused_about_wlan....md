---
title: "Slightly confused about wlan..."
date: 2008-11-27
forum: New to Ubuntu
---

### Post by speedsoda on 2008-11-27
I'm completely new to linux, ubuntu and all things related to it, and I can't at all figure out how to make my wireless card on my laptop work. I'm not really that technical either... What I want to do is to be able to connect to any nearby wireless network, I managed to find a tutorial that mentioned me going in to Applications > System > Networking, but oh dear, no such thing at all. So, I poked around some more and saw something about Xubuntu 8.10(My version) instead has a "Network manager" up in the taskbar in the top right. So I went there but it wants SSID's and other crap I know nothing about. I don't see why it's got to be that complicated considering how easy it is in vista to just bring up a list of availible networks and connect to one you like... I'm sure there's some way to achieve that simplicity in linux too, so if anyone knows how, I'd be grateful to hear everything about it... Oh, and explain like would to a three-year old... :P Also, this has been hell to write because I'm using a swedish keyboard. All buttons are weirded up, does anyone know where I can change to a swedish layout? Thanks!

Edit: Found a guide to posting wireless problem threads... Sorry about that, I'll provide information now:
Computer: Acer Aspire 5530
wireless: Atheros Communications Inc. AR242x  802.11abg
Uhh.. I don't know how to copy & paste from the terminal and the rest seems a bit much to write. Sorry for being an idiot..

---

### Post by Sub101 on 2008-11-27
When you click on the network manager applet (thats the thing that looks like 2 computers in the top right bar) what do you see?

You should see a list of nearby wireless networks?

---

### Post by Sub101 on 2008-11-27
And the keyboard would be:

System ==> preferences ==> keyboard and then click the plus, find sweden and thats it.

---

### Post by speedsoda on 2008-11-27
> **Sub101 said:**
> When you click on the network manager applet (thats the thing that looks like 2 computers in the top right bar) what do you see?

You should see a list of nearby wireless networks?

Left clicking on it does show a list, but it's only entry is the wired network I'm connected to right now by a network cable. Nothing wireless at all, and I know there are at least 3 accesible wlans in my vicinity...

> **Sub101 said:**
> And the keyboard would be:

System ==> preferences ==> keyboard and then click the plus, find sweden and thats it.

I assume you mean Applications > System > Preferences... And there's no "preferences" in the system rollout. I found something called "Language support" under system, downloaded some swedish language package, changed whatever I could to swedish from english, but I can't really see that anything has changed.
Edit: Oh, some window landed in the background and said that I'll need to re-login for the changes to take effect. Didn't see that. I'll do that and see what happens.
Edit2: Well, that sucked. It changed the language to swedish, but not the keyboard. Meh. =/
Edit3: Hey look at that. From nowhere something called "SCIM"(Smart Common Input Method) appeared up there in the right corner, where I could choose a swedish layout. It then tells me I should SCIM. I don't even know how it got started in the first place though. :P I feel like my dad when he starts pushing every button on the digital tv controller and screws up everything. Sigh.

---

### Post by GepettoBR on 2008-11-27
Right-click the network manager, and make sure "Enable wireless" is ticked.

> **speedsoda said:**
> Edit3: Hey look at that. From nowhere something called "SCIM"(Smart Common Input Method) appeared up there in the right corner, where I could choose a swedish layout. It then tells me I should SCIM. I don't even know how it got started in the first place though. :P I feel like my dad when he starts pushing every button on the digital tv controller and screws up everything. Sigh.

SCIM appears whenever you have support for more than one language installed.

---

### Post by speedsoda on 2008-11-27
> **GepettoBR said:**
> Right-click the network manager, and make sure "Enable wireless" is ticked.



SCIM appears whenever you have support for more than one language installed.

Rightclicking it shows only one "Tickable box", "Enable networking", which is ticked. 

Oh, thanks. That explains why it suddenly popped up. Annoying though, that now I rebooted to make the changed keyboard layout work I also changed back to english(Cause the swedish was more like swenglish) and then the SCIM dissapeared and I still have the english layout..:confused:

---

### Post by GepettoBR on 2008-11-27
It's posible that your wireless card isn't supported by Ubuntu without some tweaking ("out of the box"). I had to compile the drivers for mine in order for it to work (don't worry, though, it's a lot easier than it sounds).

Check here and see if your card is listed: [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by GepettoBR on 2008-11-27
It's posible that your wireless card isn't supported by Ubuntu without some tweaking ("out of the box"). I had to compile the drivers for mine in order for it to work (don't worry, though, it's a lot easier than it sounds).

Check here and see if your card is listed: [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by Bucky Ball on 2008-11-27
Copy and paste in the terminal is same but with ctl. (ie copy=ctl/c)

[http://ubuntuforums.org/showthread.php?t=902860](http://ubuntuforums.org/showthread.php?t=902860)

---

