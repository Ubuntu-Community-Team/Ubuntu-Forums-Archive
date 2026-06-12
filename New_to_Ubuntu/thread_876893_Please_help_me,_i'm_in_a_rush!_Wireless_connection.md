---
title: "Please help me, i'm in a rush! Wireless connection"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by AKsuited09 on 2008-08-01
I only have my wired connection for about two hours. I can't get my wireless connection working.

Detecting your network controller(s):

Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

I have downloaded the ndiswrapper thing and the madwifi thing, and as the ignorant noob I am i thought that would be it. But as i open the ndiswrapper-thing i get a message that i have to like enter an inf-file. I don't have the driver-CD for my network controller. I can't find anywhere to download it. 

I do not understand much of this computer-stuff, and I'm a norwegion youngster too, so my english i pretty poor. Pleas help me the best you can, you will save my day:KS

---

### Post by AKsuited09 on 2008-08-01
does anybodyhave any idea of where i can download the inf-file?

---

### Post by christianxxx on 2008-08-01
The atheros card has a solution here:
[http://ubuntuforums.org/showthread.php?t=756318](http://ubuntuforums.org/showthread.php?t=756318)

I couldn't find anything on your Broadcom card, but I suppose something could be done. Though you might need the original drivers...

---

### Post by AKsuited09 on 2008-08-01
Ok, but if i do get a hold of the original drivers, is there a chance that might be everything i need to do? I'm starting to get a bit dizzy of all this...

---

### Post by ingeva on 2008-08-01
> **AKsuited09 said:**
> I do not understand much of this computer-stuff, and I'm a norwegion youngster too, so my english i pretty poor. Pleas help me the best you can, you will save my day:KS

I have had Ubuntu for a week so I'm a quite new user myself. :)
The previous version of Ubuntu didn't allow me to go online with the wireless network, even though everything seemed to work fine.

With 8.04 all I had to do was to enter my WPA security code, switch off the computer, remove the network cable (IMPORTANT!) and then start up. Everything worked nicely from then.

I'm quite close to you so if you need further help just call 6755 0125.
I'm retired so I have all the time in the world. Well, almost, especially now that I have thrown out Windows. :)

BTW, I have a D-link card. Works as a charm. My son uses the same card on his Windows machine. On Ubuntu there was no need for additional software.

---

### Post by christianxxx on 2008-08-01
To use ndiswrapper, you will need the original drivers. 
But the solution I posted doesn't use ndiswrapper from what I could see. But you have to check to be sure.

Anyways, why do you have 2 cards? And why does you wired connection close in two hours?

---

### Post by AKsuited09 on 2008-08-01
thank you !

but where do i find the place to enter the WPA-code?
 i haven't even got the "wireless connection" tap in thew network-connections settings. only the wired-connections tab and some point-to-point thing

---

### Post by ingeva on 2008-08-01
> **AKsuited09 said:**
> thank you !

but where do i find the place to enter the WPA-code?
 i haven't even got the "wireless connection" tap in thew network-connections settings. only the wired-connections tab and some point-to-point thing

First things first!
If your computer doesn't find the network card, you WILL need a driver first. Just make sure it's a Linux driver. When you have installed that, the wireless network connection icon should appear in your main menu panel. On my screen it's in the rightmost group. When I click it the menu to connect to the various WiFi networks in my neighborhood appears.

When you select one of those you'll be asked for your security code. I strongly recommend that you set up your router to use WPA security. Enter the same code for your card.

---

### Post by AKsuited09 on 2008-08-01
But when i go to the hardware-drivers thing it finds it. Still, the wireless-sign wont occur in my network panel. I downloaded an inf-file that somebidy with a similar card and problem had been encouraged to download, and ran the inf-file in ndiswrapper. Nothing happened

---

### Post by ingeva on 2008-08-01
> **AKsuited09 said:**
> But when i go to the hardware-drivers thing it finds it. Still, the wireless-sign wont occur in my network panel. I downloaded an inf-file that somebidy with a similar card and problem had been encouraged to download, and ran the inf-file in ndiswrapper. Nothing happened

Well I'm sorry but this is beyond my knowledge. Let's hope you get better answers.

---

### Post by spencercarran on 2008-08-01
What's the output of iwconfig?

I feel your pain- the Broadcom wifi chips are a pain to get working in Linux. But it can be done!

---

### Post by AKsuited09 on 2008-08-01
it closes because i have to go home, where i have another computer who just wants to work every now and then.

nora@nora-hjemmepc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

nora@nora-hjemmepc:~$ 





Any body? More tips? What is my next step? If i find the original drivers-cd, could that be everything i need? Should i download something before i have to leave the wired connection?

---

### Post by spencercarran on 2008-08-01
All right, that means you don't have any wireless drivers right now.

You might try these links. [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") or [https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64]("https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64").

---

### Post by AKsuited09 on 2008-08-01
I have installed ndiswrapper, and in "HARDWARE DRIVERS" it decects drivers for my network card.

I really appreciate your help! I am just totally confused.

---

### Post by spencercarran on 2008-08-01
Hm. I'm really new to Ubuntu myself, so this seems to be the blind leading the blind!:-k

What hardware are you using? And how is it that you have two wireless cards? (Atheros and Broadcom?) Atheros is probably easier to set up. I'll look for an online guide for it.

EDIT: OK, here's the official Ubuntu documentation for wireless. [https://help.ubuntu.com/8.04/internet/C/wireless.html]("https://help.ubuntu.com/8.04/internet/C/wireless.html") I remember seeing a guide specifically for Atheros, but I don't remember where. Working on it, though.

---

### Post by AKsuited09 on 2008-08-01
Thanks alot. I have no idea why i have two. I just ran the hardware testing and that was what i got.

Howerer, when i run the hardware drivers-thing it only shows these atheros-stuff. "Supoport for atheros... wireless lan" and "Atheros HAL"

---

### Post by spencercarran on 2008-08-01
Probably better to try for Atheros- the only Broadcom guides I've seen are for the 43XX versions. This thread seems to detail a similar problem to yours. [http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=8114&start=0&postdays=0&postorder=asc&highlight=]("http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=8114&start=0&postdays=0&postorder=asc&highlight=") I think you have to install the restricted modules.

---

### Post by AKsuited09 on 2008-08-01
but i have already installed the ndiswrapper

---

### Post by ingeva on 2008-08-01
> **AKsuited09 said:**
> but i have already installed the ndiswrapper

This article may help you:

[http://wiki.archlinux.org/index.php/Acer_Extensa_5200](http://wiki.archlinux.org/index.php/Acer_Extensa_5200)

Look for Broadcom.

---

