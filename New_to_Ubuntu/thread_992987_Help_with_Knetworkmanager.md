---
title: "Help with Knetworkmanager"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by SVWander on 2008-11-25
A few days ago I downloaded and installed the latest Kubuntu desktop. I was impressed with its look but the other the other day I was unable to connect to my wireless router. I have researched the problem but only get confused by all the version numbers. From what I gather it is a problem with knetworkmanager. Nothing I do will open that program. Can someone tell me how I can connect to my wireless router? Is there a way to restore the original settings?

Thank you, Tim

---

### Post by cozmicharlie on 2008-11-25
OK - lets start from the beginning.  What wireless router do you have?  What version of kubuntu are you running?  Have you looked at the Hardware Drivers to see if you need to install any proprietary drivers (go to the menu>systems>Hardware Drivers).  

Wireless has greatly improved in Ubuntu but it can still be a hassle so we just need to work through it.

---

### Post by SVWander on 2008-11-25
> **cozmicharlie said:**
> OK - lets start from the beginning.  What wireless router do you have?  What version of kubuntu are you running?  Have you looked at the Hardware Drivers to see if you need to install any proprietary drivers (go to the menu>systems>Hardware Drivers).  

Wireless has greatly improved in Ubuntu but it can still be a hassle so we just need to work through it.

I have installed Intrepid in both Ubuntu and Kubuntu. Ubuntu logs on to the router without a problem and Kubuntu didn't have a problem at first then it stopped connecting. So I am writing this from inside of Ubuntu on a Dell Inspiron 1200. It uses a: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) Running off Broadcom B43 wireless driver. This at least is the driver in Ubuntu. Whatever it was it was running great at first. 

I have had great luck with the old Dell and Ubuntu! Unlike XP on this machine Ubuntu runs great and I haven't had to much trouble with the wireless card. Thank you for your help. Tell me if that is enough information. I can start a kubuntu session and copy info you might need.

Tim

---

### Post by cozmicharlie on 2008-11-25
I guess the obvious answer is to use Ubuntu.  Lets try a few things first.  I don't know why it works in Ubuntu and not kubuntu. 

What is the output when you type this in a terminal (from the computer running kubuntu)?
```
lshw -C network 
```

---

### Post by SVWander on 2008-11-25
> **cozmicharlie said:**
> I guess the obvious answer is to use Ubuntu.  Lets try a few things first.  I don't know why it works in Ubuntu and not kubuntu. 

What is the output when you type this in a terminal (from the computer running kubuntu)?
```
lshw -C network 
```

To answer your first question. I like the eye candy in Kubuntu. That might sound shallow but . . . also for some strange the screen resolution is much better.

For some reason I am able to access the router now in Kubuntu BUT knetworkmanager is not working. To connect and disconnect I have to use wifi-radar. Clicking on Knetworkmanager or trying to run it in a terminal doesn't bring the network manager up.

The output of lshw -C network:

~$ sudo lshw -C network
[sudo] password for lap1: 
  *-network               
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 0
       resources: irq:16
  *-network
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:00:25:2a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:d5:f1:f5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.4 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 5a:24:6a:99:8f:7e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by cozmicharlie on 2008-11-25
Everything looks OK in your file and if it is working then it is not a wifi card issue but it sounds like something is not working right in knetwork.  You could try reinstalling knetwork or another option is to get the latest build from the network manager maintainer.  To do that, go here [https://launchpad.net/~network-manager/+archive](https://launchpad.net/~network-manager/+archive).  To add as a repository in Synaptic go to "display source.list entries for" and use Intrepid.  Then add the two lines to your repository list.  In the menu go to system>administration>software sources>third party and add the lines one line at a time, reload and close.  Now you will have the latest version of knetwork.  Or, alternatively search the forums for this issue and see if anyone else is having problems and how they fixed it.

I hope this helps.

---

### Post by SVWander on 2008-11-26
> **cozmicharlie said:**
> Everything looks OK in your file and if it is working then it is not a wifi card issue but it sounds like something is not working right in knetwork.  You could try reinstalling knetwork or another option is to get the latest build from the network manager maintainer.  To do that, go here [https://launchpad.net/~network-manager/+archive](https://launchpad.net/~network-manager/+archive).  To add as a repository in Synaptic go to "display source.list entries for" and use Intrepid.  Then add the two lines to your repository list.  In the menu go to system>administration>software sources>third party and add the lines one line at a time, reload and close.  Now you will have the latest version of knetwork.  Or, alternatively search the forums for this issue and see if anyone else is having problems and how they fixed it.

I hope this helps.

Thank you for all your help! I guess Kubuntu is not ready for prime time. I did all you suggested but still knetworkmanager was not working. I had to use wifi-radar to connect. Someone with my technical skill than I have might be keep KDE tuned correctly but I don't seem to have enough skill. So for now I guess I will follow your other suggestion and just use Ubuntu. For older machines like mine Ubuntu cannot be beat! Again, thank you for your help.

Tim

---

### Post by cozmicharlie on 2008-11-26
OK - I wish I could have helped you solve the problem but I am out of ideas and at least you have a great alternative that works.  FYI, if you want a nicer desktop than the standard Ubuntu try this [http://tombuntu.com/index.php/2008/11/13/shiki-colors-and-community-themes-in-ubuntu-810/](http://tombuntu.com/index.php/2008/11/13/shiki-colors-and-community-themes-in-ubuntu-810/).  Not as nice as kde but better than the stock Ubuntu.

Enjoy

---

### Post by SVWander on 2008-12-02
> **cozmicharlie said:**
> OK - I wish I could have helped you solve the problem but I am out of ideas and at least you have a great alternative that works.  FYI, if you want a nicer desktop than the standard Ubuntu try this [http://tombuntu.com/index.php/2008/11/13/shiki-colors-and-community-themes-in-ubuntu-810/](http://tombuntu.com/index.php/2008/11/13/shiki-colors-and-community-themes-in-ubuntu-810/).  Not as nice as kde but better than the stock Ubuntu.

Enjoy

Thanks, I installed the desktop you suggested and it is better. Also the latest update in Kubuntu might just have fixed the knetworkmanager problem. I can switch session and KDE works. Plasma task bar or whatever they call it crashes, has to be deleted and then it will work again. Plasma still needs lots of work. Again Thanks.

Tim

---

### Post by cozmicharlie on 2008-12-02
Great - good to hear you got it all working.  KDE4 and Plasmoids are still a work in progress so you may have to bear with a few bugs for awhile.  The other option is to go back to kde3.  Personally, I like the kde4 interface enough that I don't mind a few bugs.  

Enjoy!

---

### Post by hyper_ch on 2008-12-02
I've never been happy with any network manager provided on *buntu so I did manually configure it all. However I discovered WICD and use it now as network manager. You might want to have a look at that :)

---

### Post by SVWander on 2008-12-02
> **hyper_ch said:**
> I've never been happy with any network manager provided on *buntu so I did manually configure it all. However I discovered WICD and use it now as network manager. You might want to have a look at that :)

Thanks for the info. I will check out WICD. A couple of years ago I would manually configure my wireless connection. In doing so I think I learned a lot. When Knetworkmanager went out that is how I was able to connect. 
Tim

---

### Post by hyper_ch on 2008-12-02
:) good luck :)

---

