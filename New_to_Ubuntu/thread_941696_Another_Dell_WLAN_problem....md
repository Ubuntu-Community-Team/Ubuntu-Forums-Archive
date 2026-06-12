---
title: "Another Dell WLAN problem..."
date: 2008-10-08
forum: New to Ubuntu
---

### Post by simpsonna on 2008-10-08
I've done a lot of searching on this and other forums trying to fix this but it hasn't helped.

I have a Dell 1505 with a 1390 WLAN card. I have a Dual Boot set up with Vista and Ubuntu 8.04. I can not get it to connect to the internet when I am booted in Ubuntu. I only have access to wireless in my apartment so I have to do anything with internet in Vista or go to a friends with Ethernet to do it in Linux.

I have loaded the Windows wireless drivers app and installed the bcmwl5.inf file but It didn't help.



I saw where most people wanted to know the results from this:

[PHP]lshw -C Network[/PHP]

SO here it is:
 
[PHP] *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:66:99:b1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=172.16.0.169 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:92:e9:5a:8c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g[/PHP]

Also, I usually have a light on above my keyboard when my wireless is on and it is off right now. A keyboard shortcut turns it on and off in vista, but it doesn't respond in linux right now.

Thanks for your help,
Nick

---

### Post by Idefix82 on 2008-10-08
Ubuntu is still trying to use the wrong driver b44. You need to blacklist it. Try the following commands:
```
sudo modprobe -r b44 b43
sudo modprobe ndiswrapper
sudo iwlist scan
```

and see if that brings the network up. If it does then do
```

cd /etc/modprobe.d/
gksudo gedit blacklist
```

and add the line
```
blacklist b44
blacklist b43
```
at the end, then save.

---

### Post by phidia on 2008-10-08
There is an extensive guide on your card [here]("http://ubuntuforums.org/showthread.php?t=870086&highlight=BCM4311") as well as [many other threads]("http://ubuntuforums.org/search.php?searchid=49258723") on that card in the [Networking & Wireless Forum]("http://ubuntuforums.org/forumdisplay.php?f=336").

---

### Post by simpsonna on 2008-10-08
Ok, I followed those steps and got the blacklist. I added those two lines at the bottom and save it.

But now it doesn't show any wireless option in the connections stuff? What next?

And I've been reading those how-to's and stuff. I just can't find anything relevant enough to help

Nick

---

### Post by Papa-san on 2008-10-08
Double check which drivers you need. Some 4311's use bcmwl5 and some use bcmwl5a.

---

### Post by simpsonna on 2008-10-08
> **Papa-san said:**
> Double check which drivers you need. Some 4311's use bcmwl5 and some use bcmwl5a.

How do I do that? Like I said, 

> I have loaded the Windows wireless drivers app and installed the bcmwl5.inf file but It didn't help.

I could be doing it wrong I guess.

I'm not a computer idiot exactly but Linux is very new to me and I'm not a programmer by any means.:(

---

### Post by Papa-san on 2008-10-08
I had never even thought about any Linux distro until about two and a half years ago. I got frustrated with Windows XP because they wouldn't allow me to install my legally purchased copy on a laptop I had purchased. Supposedly because I had already transferred it to three other systems. (And taken it off... I don't pirate stuff or use cracks... I do it legally.)

I did the Ubuntu thing all at once before I knew anything, and some of these guys can tell you some stories about my ineptitude and frustration... I am a 'convert', and became so WAY to fast and unprepared! My first post was: "Ummm... What is a 'terminal'? and where do I find it?"

I can feel your pain! lol

OK, that said: if you have blacklisted the b43 and b44 drivers, you should be able to run```
sudo lshw -C network
``` and re-post the output. If you look in your earlier post, you will see where the network controller driver is listed as b43. ```
*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: **[COLOR="Red"]driver=b43[/COLOR]**-pci-bridge latency=0 module=ssb 
```Let's see if it has changed now...

Oh... is the wireless light on at all? If not, try pressing 'Fn+F2' see if it comes on...

---

### Post by knix on 2008-10-08
1) b43 does not work well.
2) You would have to install ndiswrapper, then the .inf with ndiswrapper to use ndiswrapper
3) wl is the new native driver from Broadcom. It works great, and you don't have to muck around much. Here's how to install it [http://ubuntuforums.org/showthread.php?t=880218]("http://ubuntuforums.org/showthread.php?t=880218")
It's installed by default in Intrepid, which is what I'm using, so I haven't had to install it. Basically all you have to do is update your linux-image and linux-restricted-modules, restart, and enable it in the driver manager (in theory)
That said, it conflicts with b43 and ssb; you'll have to do something like this every time you boot (just put it in your /etc/rc.local before the exit 0)

modprobe -r b43
modprobe -r b44
modprobe -r ssb
modprobe -r wl
modprobe wl
modprobe b44

you remove b44 because it uses ssb (now you can remove ssb)
you remove wl just in case- I'm not sure if you have to do this
you insert wl
you insert b44 so your wired network will work. This will load ssb again, but this is fine because wl was loaded beforehand.

wl makes my killswitch work as well.

---

### Post by anewguy on 2008-10-08
I believe, unless it has changed with the release change, that you also still need to blacklist bcm43xx.

As for your driver files, do you have the drivers (for XP hopefully!) that came with your PC, or are you able to download them from Dell?  You should be able to get the exact driver files from Dell for your serial number.  Given those, and running any kind of extract or unzip needed, you should see that valid drivers for your card to use with ndiswrapper.

Also, as others have pointed out in other posts, if you are new to Linux, there is a GUI'd front end to ndiswrapper called ndisgtk.  Some people have better luck getting things to work using it instead of the command line interface to ndiswrapper.  The ndisgtk package should be available from the installation CD or via Synaptics package manager.

Dave :)

---

### Post by Papa-san on 2008-10-08
Oops! hehe... :-)<-- sheepish grin!

Listen to the 'new' guy! I forgot about bcm43xx... It has to go too...

---

### Post by Idefix82 on 2008-10-09
> **knix said:**
> 

modprobe -r b43
modprobe -r b44
modprobe -r ssb
modprobe -r wl
modprobe wl
modprobe b44


Two things: first you need to start each line with sudo.
Second: you can combine the first four lines into one:
```
sudo modprobe -r b43 b44 ssb wl
```

---

### Post by simpsonna on 2008-10-09
Thanks guys, yesterday I did a lot of searching through old posts and how-to's and one thing worked.

Someone said there was a bug in 8.04 that prevents ndiswrapper from working properly and gave a line of code to fix it. Somewhere around that time It started working. haha. I put that code in like 5 times before it stuck. But it's working now! Yay!

But my adobe flash player isn't :(  

I have gotten rid of all the flash packages in the synaptic package manager but the flashplugin-nonfree and i have tried to install the driver from the flash player website. No luck. I am running a 64 bit system and a friend of mine thinks that is screwing it up but I don't know.

---

