---
title: "Compiz and power consumption"
date: 2015-11-24
forum: New to Ubuntu
---

### Post by shannon5 on 2015-11-24
So I recently moved to Ubuntu from Windows 10 both on my desktop and my laptop (an Asus Zenbook ux305).  I'm very happy with Ubuntu on my desktop, but I noticed that 'Compiz' is chewing up power on my laptop.  I tried installing the Lubuntu desktop because I heard it was lighter, however I didn't like it much.  I tried the Gnome-fallback-desktop and that also wasn't as nice as Unity for me.

I'd really like to just disable Compiz and keep the functionality of Unity. I tried disabling all the effects in compiz with compiz manager but it still didn't stop compiz from dominating my system in a most embarrassing fashion.  I looked into something called 'The Unity 2D desktop', but that seems to be a dummy package with no data.

I'd really appreciate any help on getting a simple desktop with the layout and workings of Unity but without the power sucking graphical frills.

---

### Post by grahammechanical on 2015-11-24
On Ubuntu Compiz is the compositor/window manager and Unity is a Compiz plugin. So, no Compiz = no Unity. It is a fact of Ubuntu life.

What makes you think that Compiz is "chewing up power?" Have you run the top command? On my machine with an Intel core2 duo 2.40GHz CPU and 1 GB RAM Compiz will use anything between 0.7% and 7.6% CPU depending on the work that it has to do. It will quickly reduce CPU useage if nothing much is happening.

Unity 2D was a fallback option for Ubuntu 12.04 that used Metacity as the window manager for machines with graphic adapters that could not do hardware accelerated 3D rendering. It has been discontinued because it is replaced by an open source video driver called llvmpipe.

You might want to look at Ubuntu Mate. That will let you run on either Compiz or Metacity and it has a large set options for modifying the user interface. You might come close to to Unity with Ubuntu Mate.

Regards.

---

### Post by shannon5 on 2015-11-24
> **grahammechanical said:**
> 
What makes you think that Compiz is "chewing up power?" Have you run the top command? 

Yeah, I spent some time watching PowerTop and Top, and Compiz was up there all the time.

Anyway, thanks for the reply, I'll go check into Mate.

If anyone else has anything to add I'd love more info. I'm also wondering if Canonical is going to put more work into making Linux less power hungry on laptops. Right now, sadly, Windows 10 is beating it for efficiency of power consumption.

---

### Post by mc4man on 2015-11-25
> **shannon5 said:**
> 

If anyone else has anything to add I'd love more info. I'm also wondering if Canonical is going to put more work into making Linux less power hungry on laptops. Right now, sadly, Windows 10 is beating it for efficiency of power consumption.
You could mention your hardware.
By default there are no real 'frills' enabled, though old hardware could struggle a bit with Ubuntu. Unity has a low graphic mode though may not be user settable in whatever release of ubuntu you are using. Screen from 16.04

As mentioned compiz doesn't use much cpu resources when being used, when   not like writing for instance this post then practically none.

---

### Post by shannon5 on 2015-11-25
> **mc4man said:**
> You could mention your hardware.

As I said, it's not a hardware concern, it's about maximizing battery life on my laptop.  I have an Asus Zenbook ux305 with 8gig ram.  It runs Unity with no trouble whatsoever. The problem is that unity drains my battery in half the time that Windows 10 does.  I got very good results with the Lubuntu desktop. I really like the Unity desktop though as I use it on my Desktop PC and I would like to keep the functionality, I just don't need the graphical frills that Compiz provides. I was hoping to reduce the power consumption significantly by reducing the effects.  Unfortunately even when I installed Compiz manager and turned off as many effects as I could, Compiz is still hammering my processor.

My hardware is listed below if you still want to see it:

[h=3]Spec Sheet[/h]
[LIST]
[*][[FONT=inherit][COLOR=#009900][FONT=inherit]_CPU_[/FONT][/COLOR][IMG]http://images.intellitxt.com/ast/adTypes/icon1.png[/IMG][/FONT]]("http://www.techradar.com/reviews/pc-mac/laptops-portable-pcs/asus-zenbook-ux305-1264384/review/2#"): 800MHz Intel Core M 5Y10 (dual-core, 4MB cache, 2GHz with Turbo Boost)
[*]Graphics: HD Graphics 5300
[*]RAM: 8GB DDR3
[*]Screen: 13.3-inch FHD 1,920 x 1,080 (matte)
[*]Storage: 256GB SSD
[*]Ports: 3 x USB 3.0, micro HDMI, SD card slot, headphone/microphone combo jack
[*]Connectivity: 802.11n + Bluetooth 4.0
[*]Camera: 1.2MP HD webcam
[*]Weight: 2.6 pounds
[*]Size: 12.8 x 8.9 x 0.5 inches (W x D x H)
[*]
[/LIST]

---

