---
title: "Wireless HP Mini 1000 won't work with Ubuntu 12.04"
date: 2013-08-19
forum: New to Ubuntu
---

### Post by torgunn on 2013-08-19
[FONT=Courier 10 Pitch]Hi! I'm new to Ubuntu, or rather, I'm new to the terminal, so I'm hoping this isn't answered in another thread. I've been at it for two days now, can't seem to figure this out, although I've read everything I can come across. I'm having trouble getting my wireless working with Ubuntu 12.04[/FONT]


[FONT=Courier 10 Pitch]I have a HP mini 1000 which I've been running with Ubuntu for about a year and I've had no problems with wireless. However, I reinstalled it a couple of days ago and now I can't get the wireless up and running. I've tried installing the fwcutter-b43-installer, but it still doesn't work. I'm wondering if I maybe need to download somefirm warefiles? The biggest problem is that there's no way I can get an Internet connection without the wireless, and it seems I'm notable to fix it without. I have another computer with Internet though,so I've been transferring files with a USB.[/FONT]


[FONT=Courier 10 Pitch]What confuses me the most is that the switch for the wifi (a little thingyon the side which is blue when wireless is enabled, and red when it'snot), is working perfectly. When I turn it on the rfkill list looks like this:[/FONT]


```
[FONT=Courier 10 Pitch]x@x:~$rfkill list all [/FONT]
[FONT=Courier 10 Pitch]0: hci0:Bluetooth [/FONT]
[FONT=Courier 10 Pitch]    Softblocked: no [/FONT]
[FONT=Courier 10 Pitch]    Hardblocked: no [/FONT]
[FONT=Courier 10 Pitch]1:hp-wifi: Wireless LAN [/FONT]
[FONT=Courier 10 Pitch]    Softblocked: no [/FONT]
[FONT=Courier 10 Pitch]    Hardblocked: no [/FONT]
[FONT=Courier 10 Pitch]2:hp-bluetooth: Bluetooth [/FONT]
[FONT=Courier 10 Pitch]    Softblocked: no [/FONT]
[FONT=Courier 10 Pitch]    Hardblocked: no [/FONT]


[FONT=Courier 10 Pitch]and when I turn it of it looks like this:[/FONT]


[FONT=Courier 10 Pitch]x@x:~$rfkill list all[/FONT]
[FONT=Courier 10 Pitch]1:hp-wifi: Wireless LAN[/FONT]
[FONT=Courier 10 Pitch]    Softblocked: no[/FONT]
[FONT=Courier 10 Pitch]    Hardblocked: yes[/FONT]
[FONT=Courier 10 Pitch]2:hp-bluetooth: Bluetooth[/FONT]
[FONT=Courier 10 Pitch]    Softblocked: no[/FONT]
[FONT=Courier 10 Pitch]    Hardblocked: yes[/FONT]


[FONT=Courier 10 Pitch]So somehow it must know that the device exits?[/FONT]




[FONT=Courier 10 Pitch]Well,anyway, here's the lspci (which is the info about the divice, am Iright?)[/FONT]


[FONT=Courier 10 Pitch]x@x:~$lspci -vnn -d 14e4: [/FONT]
[FONT=Courier 10 Pitch]01:00.0Network controller [0280]: Broadcom Corporation BCM4312 802.11b/gLP-PHY [14e4:4315] (rev 01) [/FONT]
[FONT=Courier 10 Pitch]    Subsystem:Hewlett-Packard Company Device [103c:1508] [/FONT]
[FONT=Courier 10 Pitch]    Flags:bus master, fast devsel, latency 0, IRQ 16 [/FONT]
[FONT=Courier 10 Pitch]    Memoryat feafc000 (64-bit, non-prefetchable) [size=16K] [/FONT]
[FONT=Courier 10 Pitch]    Capabilities:<access denied> [/FONT]
[FONT=Courier 10 Pitch]    Kerneldriver in use: b43-pci-bridge [/FONT]
[FONT=Courier 10 Pitch]    Kernelmodules: ssb [/FONT]
```


[FONT=Courier 10 Pitch]I have a ton of other information from the terminal, but I'm not sure what is relevant?[/FONT]


[FONT=Courier 10 Pitch]Anyway,thanks for taking the time to read this, I'll keep trying, but I'd be ecstatic if someone could help me :)

* sorry about the weird contracted words, got messed up when I pasted it in from the writer document, now it's fixed[/FONT]

---

### Post by kurt18947 on 2013-08-19
I'd suggest that if you have a way to do it, download and create an Xubuntu live USB.  I have the same machine and it works very well with 32 bit Xubuntu.  I wonder if your reinstall was with 12.04.2 which has the 3.5.x kernel rather than 3.2.x of 12.04.  I had some issues with 12.10/3.5.x kernel though I didn't try that on the HP, figuring Xubuntu was better suited to the specs of the machine.  Lubuntu would be another choice in the *buntu family.

---

### Post by torgunn on 2013-08-19
Thank you! I've installed xubuntu now. It reckognizes the wireless device (hurray!), but it's grey and it says: "device not ready (firmware missing)"

Is this the same problem as in ubuntu?

* Maybe I should more precise in my question, is it the firmware-b43-installer file that's missing?

** I've been searching around a bit, I think part of the problem is that I've had the wrong firmware-b43-installer. I missed the part which says LP-PHY, stumbled by a chance upon a thread which pointed out that theese devices need another installer. I've downloaded the file, created a directory and put it there, and then tried sudo apt-get install, it'seems like it's loading but then I get this:

Reading package list... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package [location]

I also got the same message when I tried to install the firmware-b43-installer instead. I found a lot of threads about this problem, but it seems I need to do an apt-get update, which isn't possible without internet. I'm going to try to find someone with a mobile internet-thingy, hopefully I can get internet to work, and then maybe this problem can be solved.

---

### Post by wildmanne39 on 2013-08-19
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by wildmanne39 on 2013-08-19
Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
if you get any errors please take note of them and continue with the rest of the commands.
Thanks

---

### Post by torgunn on 2013-08-20
Wow! It started working instantly! Thank you so much the both of you :)

To anyone one encountering the same problem after the installation is complete follow Wild Man's post. Wonderful!


[COLOR=#006400][SIZE=1]* As I've described in a post further down the page, I couldn't get the device to work in Ubuntu. There's probably a solution to this probelm aswell, but after three days of constant terminal failure, I took the easy way out and installed Xubuntu instead.[/SIZE][/COLOR]

---

### Post by Vladlenin5000 on 2013-08-20
The instructions work for any Ubuntu or Debian flavor. Xubuntu or Lubuntu are better suited for your machine because they aren't so resources hungry as the plain Ubuntu (Unity desktop) but the issue with the Broadcom firmware is exactly the same.

In similar situations I either connect an Ethernet cable if available or use an external (USB) WiFi dongle that is natively supported like the ones based on the Realtek 8191SU chipset (highly recommended).

---

### Post by torgunn on 2013-08-20
> **Vladlenin5000 said:**
> The instructions work for any Ubuntu or Debian flavor. Xubuntu or Lubuntu are better suited for your machine because they aren't so resources hungry as the plain Ubuntu (Unity desktop) but the issue with the Broadcom firmware is exactly the same. 

You're probably right, my guess is you know a lot more about this. I don't know if I did something wrong, tried installing it with Ubuntu first, but it couldn't find the device. When I later installed Xubuntu, it was detected right away during the installation. It's probably my one fault though, I'll change the previous post :)

---

### Post by matt54 on 2014-02-04
This answer was exactly what I needed for my old HP Mini 1000. Thanks!

---

### Post by aproposjnr on 2014-05-15
I really wanted to thank you for this answer, I have never used Xubuntu before and couldn't find the drivers I needed anywhere on: [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

Anyways, really appreciate the time and effort that alot of members seem to contribute on these forums.

-Apropos

---

### Post by william32 on 2014-05-30
Thank you! Wild Man.
The code and zip package work perfectly on Lubuntu 14.04.

---

