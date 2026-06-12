---
title: "Installing packages and wireless connection"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by elzorroviejo on 2008-06-08
OK, I have a new laptop: Gateway MX8738. I have made it a dual boot system (keeping the Vista installation until I am sure I have Linux configured and stable. I have installed the latest Linux kernel (2.6.24.18) and the Hardy flavor of Ubuntu. I have been using computers since I took a course in Fortran some 32 years ago. However, the last 16 years or so have been spent in an almost exclusively Windows environment. So, while the command line does bring back vague memories of DOS, the emphasis is on the word "vague". 

My first problem lies in the area of wireless connection. This laptop comes equipped with a RealTek RTL8187 built-in USB wireless card. When I initially installed Linux and Ubuntu, I had intermittent wireless connectivity. In trying to make the "intermittent" less intermittent and more permanent, I tried to install Ndiswrapper, but had the wrong driver or something. 

Now, when I do a 

sudo lshw -C network command, I get the following back:

 *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:c0:a8:e9:4b:9d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

It would appear that I have made any drivers I once had disappear. Now, I went to RealTek's website and d/l'd a driver file named RTL8187_linux26.1025.0328.2007 which is now sitting on my desktop. This package contains a READ-ME file which gives instructions for installing the drivers...except they could be in Greek for all I get out of them. No, I exaggerate. What I need to know is what directory the drivers need to go into and then how do I get them there. 

I figure that if I can at least get wlan0 outfitted with drivers, then I can go try the instructions over in the Networking part of the forum which are supposed to help get the RealTek cards working. 

I do have my wired connection working on this machine, but, after all, its a laptop and I would like to take it out on the patio every now and again and connect to the internet while enjoying a nice summer's evening. Is that too much to ask? 

Thanks for any help anyone might be able to offer.

---

### Post by Unix_Slayer on 2008-06-08
> **elzorroviejo said:**
> OK, I have a new laptop: Gateway MX8738. I have made it a dual boot system (keeping the Vista installation until I am sure I have Linux configured and stable. I have installed the latest Linux kernel (2.6.24.18) and the Hardy flavor of Ubuntu. I have been using computers since I took a course in Fortran some 32 years ago. However, the last 16 years or so have been spent in an almost exclusively Windows environment. So, while the command line does bring back vague memories of DOS, the emphasis is on the word "vague". 

My first problem lies in the area of wireless connection. This laptop comes equipped with a RealTek RTL8187 built-in USB wireless card. When I initially installed Linux and Ubuntu, I had intermittent wireless connectivity. In trying to make the "intermittent" less intermittent and more permanent, I tried to install Ndiswrapper, but had the wrong driver or something. 

Now, when I do a 

sudo lshw -C network command, I get the following back:

 *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:c0:a8:e9:4b:9d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

It would appear that I have made any drivers I once had disappear. Now, I went to RealTek's website and d/l'd a driver file named RTL8187_linux26.1025.0328.2007 which is now sitting on my desktop. This package contains a READ-ME file which gives instructions for installing the drivers...except they could be in Greek for all I get out of them. No, I exaggerate. What I need to know is what directory the drivers need to go into and then how do I get them there. 

I figure that if I can at least get wlan0 outfitted with drivers, then I can go try the instructions over in the Networking part of the forum which are supposed to help get the RealTek cards working. 

I do have my wired connection working on this machine, but, after all, its a laptop and I would like to take it out on the patio every now and again and connect to the internet while enjoying a nice summer's evening. Is that too much to ask? 

Thanks for any help anyone might be able to offer.

Hmmmmmmmmm........  I think I know what's your problem. Your adapter is there, and working. Your cat5 cable needs to be disconnected from your wired card. It's finding the internet connection through eth0, and not wlan0. Give it a try. It should look close to this as follows:
```
*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:e5:da:93:86
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2870 driverversion=1.52+Linksys, A Division of Cisc ip=192.168.0.102 link=yes multicast=yes wireless=IEEE 802.11g
```

---

### Post by elzorroviejo on 2008-06-08
Thanks for the reply, however, my problem is not the cat5 connection. My problem is that I've managed to delete the drivers for the RealTek card. Or maybe the original drivers were commented out when I tried to install Ndiswrapper. Or maybe my problem is that I am not looking in the right place to find the original drivers. They would be in which directory? And then I have the package I downloaded from RealTek with what they claim to be Linux drivers for the RTL8187 card...but I'm not sure if these are for the PCI card or the USB card or both...or neither because I have seen some comments about a bug in the RealTek drivers. 

So, I think what I need is to get this package installed so I can see if these drivers work. If "yes", then my quest is done. If "no", then I move on to Plan B (which I am currently developing...*grin*). Sound reasonable? Any comments, suggestions, authoritative directions? All contributions gratefully accepted!

---

### Post by Unix_Slayer on 2008-06-08
> **elzorroviejo said:**
> Thanks for the reply, however, my problem is not the cat5 connection. My problem is that I've managed to delete the drivers for the RealTek card. Or maybe the original drivers were commented out when I tried to install Ndiswrapper. Or maybe my problem is that I am not looking in the right place to find the original drivers. They would be in which directory? And then I have the package I downloaded from RealTek with what they claim to be Linux drivers for the RTL8187 card...but I'm not sure if these are for the PCI card or the USB card or both...or neither because I have seen some comments about a bug in the RealTek drivers. 

So, I think what I need is to get this package installed so I can see if these drivers work. If "yes", then my quest is done. If "no", then I move on to Plan B (which I am currently developing...*grin*). Sound reasonable? Any comments, suggestions, authoritative directions? All contributions gratefully accepted!

Wait a second. if those drivers from RealTek are linux drivers, you would have no reason to use ndiswrapper. I don't think ndiswrapper would let you add a device with a linux driver.

---

### Post by elzorroviejo on 2008-06-08
No, no, no..."What we have here is a failure to communicate." The Ndiswrapper was only mentioned because in my abortive attempt to install a driver using it, I managed to make the original drivers disappear (or maybe they didn't; maybe I just don't know where to find them.) My download of the Linux driver package was after the Ndiswrapper episode. As far as I can tell, all that package has done is sit on my desktop waiting patiently for me to figure out what to do with it. 

So, let's take stock here:
           1) When I originally installed Ubuntu 7.10 onto my Gateway laptop, the Realtek RTL8187 card work...intermittently and when it did work, it was slow. (Aside: I have a Verizon FIOS Internet connection which is very, very fast.) 
           2) In my initial attempt to install a more stable driver, I used Ndiswrapper and a Windows driver downloaded from the RealTek site. This attempt did not work (I think I used the wrong driver...) 
           3) I have commented out all the instances of Ndiswrapper that I could find, which has resulted in "lshw -C network" at least being able to see the card. However, when it does see the card, there is no driver listed in the command's output
           4) I have now downloaded another driver package from Realtek. This package purports to be drivers for the RTL 8187 wireless nic. However, the attempts I have made to move it using the graphical tools on the Gnome desktop have all been soundly rebuffed, so, what I need to learn is both how and where to move this package so I can unpack it and load the included driver(s). Once I have these loaded, I will unplug the cat5 cable (through which I am now communicating) and reboot the machine to see if these drivers get the nic's attention. As I said earlier, if it does solve the problem, then we hold a quiet little celebration here in the ancestral manse (well, actually not, but I thought the picture was worth the slight embellishment...), and then move on to the next bit that I have to learn about this O/S. 

Does that make sense?

---

### Post by Unix_Slayer on 2008-06-09
> **elzorroviejo said:**
> No, no, no..."What we have here is a failure to communicate." The Ndiswrapper was only mentioned because in my abortive attempt to install a driver using it, I managed to make the original drivers disappear (or maybe they didn't; maybe I just don't know where to find them.) My download of the Linux driver package was after the Ndiswrapper episode. As far as I can tell, all that package has done is sit on my desktop waiting patiently for me to figure out what to do with it. 

So, let's take stock here:
           1) When I originally installed Ubuntu 7.10 onto my Gateway laptop, the Realtek RTL8187 card work...intermittently and when it did work, it was slow. (Aside: I have a Verizon FIOS Internet connection which is very, very fast.) 
           2) In my initial attempt to install a more stable driver, I used Ndiswrapper and a Windows driver downloaded from the RealTek site. This attempt did not work (I think I used the wrong driver...) 
           3) I have commented out all the instances of Ndiswrapper that I could find, which has resulted in "lshw -C network" at least being able to see the card. However, when it does see the card, there is no driver listed in the command's output
           4) I have now downloaded another driver package from Realtek. This package purports to be drivers for the RTL 8187 wireless nic. However, the attempts I have made to move it using the graphical tools on the Gnome desktop have all been soundly rebuffed, so, what I need to learn is both how and where to move this package so I can unpack it and load the included driver(s). Once I have these loaded, I will unplug the cat5 cable (through which I am now communicating) and reboot the machine to see if these drivers get the nic's attention. As I said earlier, if it does solve the problem, then we hold a quiet little celebration here in the ancestral manse (well, actually not, but I thought the picture was worth the slight embellishment...), and then move on to the next bit that I have to learn about this O/S. 

Does that make sense?

Ok.... I am using a RTL driver. I have a Linksys USB dual Band adapter. I installed ndiswrapper. Then I started ndiswrapper in a terminal window. When the gui came up, I hit add a device. I used a WinXP .inf file from the linksys cd that came with the adapter. As simple as that.

---

### Post by cariboo on 2008-06-09
There are drivers for your wireless card in the kernel, So you shouldn't have to use ndiswapper for the driver. Ndiswrapper is just what it says it is a wrapper to use windows drivers in linux. When I got my first wireless card about 8 years ago there were no linux drivers at all for the Broadcom chipsets. The only way to get to work was the windows driver in conjuction with ndiswrapper. 

The way to find if the drivers is loaded. In a terminal type:

```
sudo lsmod | grep rtl8187
```

if it is there it is just a matter of setting up your connection. If it isn't there, in a terminal type:

```
sudo modprobe rtl8187 
```

and you should be good to go.

Jim

---

### Post by Unix_Slayer on 2008-06-09
> **cariboo907 said:**
> 
The way to find if the drivers is loaded. In a terminal type:

```
sudo lsmod | grep rtl8187
```

if it is there it is just a matter of setting up your connection. If it isn't there, in a terminal type:

```
sudo modprobe rtl8187 
```

and you should be good to go.

Jim

It's not there. That's why I used ndiswrapper.

---

### Post by cariboo on 2008-06-09
I see the module in /lib/modules/2.6.24-16-generic and /lib/modules/2.6.24-18-generic so if you do as I suggested and use:

```
sudo modprobe rtl8187
```

That will install the module you need.

Jim

---

### Post by Unix_Slayer on 2008-06-09
> **cariboo907 said:**
> I see the module in /lib/modules/2.6.24-16-generic and /lib/modules/2.6.24-18-generic so if you do as I suggested and use:

```
sudo modprobe rtl8187
```

That will install the module you need.

Jim

My adapter is a Linksys USB model WUSB600N with dual band. I'm not using the same chip as the wusb300n. I can get both to work without wicd. Which seems to not work for me. Is the rtl8187 used for specific adapters other than the two I mentioned.

---

### Post by gm1-74 on 2011-11-29
Hi:

This is my first post, so my apologies in advance if anyhow I'm bothering too much. I do have a Laptop Gateway MX8738 that while I did upgrade from 11.04 to 11.10, at the newest distro the 11.10 distro keeps disconnecting my Internet connection constantly at similar intervals, like 10-15 mins at time.

My wireless card is a Realtek 8185.

---

