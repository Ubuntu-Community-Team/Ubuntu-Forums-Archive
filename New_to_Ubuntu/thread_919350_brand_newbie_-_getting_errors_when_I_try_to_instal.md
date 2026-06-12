---
title: "brand newbie - getting errors when I try to install ndiswrapper"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by OccamsShaver on 2008-09-13
This is frustrating! 
I installed Wubi to see if I would want to start running Ubuntu. Like many, I have had trouble getting  my wireless working (Broadcom integrated into my Presario V6000 laptop). I've waded through pages and pages of info on the web, to no avail. I tried installing ndiswrapper 1.53, but get errors when I try the "make" and "make install" commands, stating that permission is denied, and [install] Error 1, [install]Error 2

There has got to be a better way to get my wireless working... 
any ideas?

Thanks!

---

### Post by wolfen69 on 2008-09-13
did you do *sudo* make install?

---

### Post by Gannon8 on 2008-09-13
Do you even need to compile ndiswrapper? Why not just:
```
sudo apt-get install ndiswrapper-common
```
Actually, it should be preinstalled (Right?)

Anyway, you need the package "build-essentials" to compile stuff.
```
sudo apt-get install build-essentials
```
And you may need to run ./configure from the source directory.

---

### Post by OccamsShaver on 2008-09-13
> **Gannon8 said:**
> Do you even need to compile ndiswrapper? Why not just:
```
sudo apt-get install ndiswrapper-common
```
Actually, it should be preinstalled (Right?)

Anyway, you need the package "build-essentials" to compile stuff.
```
sudo apt-get install build-essentials
```
And you may need to run ./configure from the source directory.

I did try sudo make install. Unfortunately, I don't know how to do a screen capture, but it gave many many lines of text with numerous errors and warnings, concluding with error 1.

I tried sudo apt-get install ndiswrapper-common
and got "E: couldn't find package ndiswrapper-common"
I tried sudo apt-get install build-essentials
and got "E: couldnt find package build-essentials"

Mind you that machine is not connected to the internet now (no wireless). Are these commands internet-based?

---

### Post by cariboo on 2008-09-13
Build-essentials and ndiswrapper are on the hardy cd. Make sure the cd is enabled. Go To System-->Administration-->Software Sources to enable the cd. Then you can install ndiswrapper-utils, ndiswrapper-common and ndisgtk.

Jim

---

### Post by OccamsShaver on 2008-09-14
> **cariboo907 said:**
> Build-essentials and ndiswrapper are on the hardy cd. Make sure the cd is enabled. Go To System-->Administration-->Software Sources to enable the cd. Then you can install ndiswrapper-utils, ndiswrapper-common and ndisgtk.

Jim

I think I am lacking all of the prerequisite knowledge for this. I don't have a hardy cd (not even sure what that is). I did wind up plugging an ethernet cable into the laptop with Ubuntu and was able to download some of those components (admittedly having no clue what i was doing). I found instructions online for installing this particular Broadcom adapter but it still didn't work. What web site would you recommend as an approachable primer of Ubuntu basics?
Thanks again

---

### Post by caljohnsmith on 2008-09-14
> **OccamsShaver said:**
> I think I am lacking all of the prerequisite knowledge for this. I don't have a hardy cd (not even sure what that is). I did wind up plugging an ethernet cable into the laptop with Ubuntu and was able to download some of those components (admittedly having no clue what i was doing). I found instructions online for installing this particular Broadcom adapter but it still didn't work. What web site would you recommend as an approachable primer of Ubuntu basics?
Thanks again
If you post a link to the tutorial you followed, we might be able to help you better. And when you say it didn't work, if you can give more specifics in terms of errors and such, that would greatly help troubleshoot your problem.

---

### Post by OccamsShaver on 2008-09-14
> **caljohnsmith said:**
> If you post a link to the tutorial you followed, we might be able to help you better. And when you say it didn't work, if you can give more specifics in terms of errors and such, that would greatly help troubleshoot your problem.

Here is the tutorial I followed: [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/")

This time through, I did not get any errors. It seems that my Broadcom 94311MCG is now recognized. However, I have not been able to connect to my wireless network (with WPA password). One screen shows the status of the BCM B43 driver and "enabled" is not checked, but it does say "in use".
I'm not sure if it's just an issue of configuring it at this point, or if it still isn't really installed. BTW, the blue wireless LED on my laptop remains off (red).

Thanks

---

### Post by Gannon8 on 2008-09-14
Try making it now. You need build-essentials to compile anything. For your reference, a Hardy/Ubuntu CD is the CD that you install Ubuntu from.

---

### Post by doctorbighands on 2008-09-14
> **OccamsShaver said:**
> Here is the tutorial I followed: [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/")

This time through, I did not get any errors. It seems that my Broadcom 94311MCG is now recognized. However, I have not been able to connect to my wireless network (with WPA password). One screen shows the status of the BCM B43 driver and "enabled" is not checked, but it does say "in use".
I'm not sure if it's just an issue of configuring it at this point, or if it still isn't really installed. BTW, the blue wireless LED on my laptop remains off (red).

Thanks

There's a wireless indicator LED on my HP laptop that has never lit in Ubuntu. My "mute" button has an LED also, and it's never lit. I always chalked this up to a driver issue. It's never affected functionality.

EDIT: Also, welcome to the wonderful world of WiFi in Linux. Please don't let it be an indication of how solid or functional Ubuntu is; it isn't the fault of the software that Wireless is such an issue. Keep cool (I say as I admit that my frustration threshold is quite low), stick with it, and you'll get it figured out!

---

### Post by OccamsShaver on 2008-09-14
Thanks. What did you mean by "try making it now"?
Ok, I ran "lshw" and it says that the wireless card is disabled:
*-network DISABLED

Any ideas on how I can activate this?

Thanks for the encouraging words re: Linux, as I am contemplating giving up with it since I can't even get the most basic aspect (wifi) working.

---

### Post by doctorbighands on 2008-09-14
It turns out that WiFi is far from the most basic issue in Linux; in fact, it may well be the most troublesome, along with certain video drivers (at least, from what I've seen). Nonetheless, in most cases, it works out.

Let's start over from the beginning.

Place an Ubuntu CD into your drive. Once it spins up, you should receive a dialog box asking if you want to start the package manager. Do that.

Once Synaptic Package manager opens, click "Search" and search for ndiswrapper. Three items should come up; mark "ndisgtk" for installation, and  the others that you need will be marked automatically. Click "Apply," and wait for the apps to install.

When finished, click System > Administration > Windows Wireless Drivers. This opens up the Ndiswrapper application. This should be fairly self-explanatory, assuming you know the location of the .inf driver file you need. Use this application to install the driver.

After this is done, you *should* be up and running. If not, we can troubleshoot from there!

---

### Post by OccamsShaver on 2008-09-14
> **doctorbighands said:**
> It turns out that WiFi is far from the most basic issue in Linux; in fact, it may well be the most troublesome, along with certain video drivers (at least, from what I've seen). Nonetheless, in most cases, it works out.

Let's start over from the beginning.

Place an Ubuntu CD into your drive. Once it spins up, you should receive a dialog box asking if you want to start the package manager. Do that.

Once Synaptic Package manager opens, click "Search" and search for ndiswrapper. Three items should come up; mark "ndisgtk" for installation, and  the others that you need will be marked automatically. Click "Apply," and wait for the apps to install.

When finished, click System > Administration > Windows Wireless Drivers. This opens up the Ndiswrapper application. This should be fairly self-explanatory, assuming you know the location of the .inf driver file you need. Use this application to install the driver.

After this is done, you *should* be up and running. If not, we can troubleshoot from there!

Ah ok. I don't have an Ubuntu CD (I installed it as Wubi), so I am downloading at this very moment (assuming you mean the CD on the "Get Ubuntu" page). I'll post my follow up after I follow your directions.

---

### Post by doctorbighands on 2008-09-14
> **OccamsShaver said:**
> Ah ok. I don't have an Ubuntu CD (I installed it as Wubi), so I am downloading at this very moment (assuming you mean the CD on the "Get Ubuntu" page). I'll post my follow up after I follow your directions.

Yep, that's the CD I mean. Good luck - hopefully it works without a hitch! You'll find that once your wireless is up and running, everything else "just works," and you'll lurve it. :)

EDIT: I just noticed that I should probably make something in the previous instructions a bit more clear. The first instruction should (more accurately) read: "Place an Ubuntu CD into your drive *with Ubuntu already running.*" This as opposed to placing it in your drive and booting from it, which isn't what I meant, and won't help you at this point. You probably already figured all of this out, but I just wanted to be clear.

---

### Post by doctorbighands on 2008-09-14
Something else just occurred to me: If you're downloading the Ubuntu CD, then you have an active connection! If that's so, then you can effectively skip the CD altogether. It might be nice to have one on hand, but for this task, you won't need one as long as you can get online.

So, the directions are changed a bit, if you're using your currently-active connection:

Open System > Administration > Synaptic Package Manager, hit the search button, and follow my above directions from there.

You might try hitting the Reload button in Synaptic, just to be sure. If you search for "ndiswrapper" and turn up nothing, it's a simple workaround.

---

### Post by OccamsShaver on 2008-09-14
I've been posting these messages from my laptop in Win XP... I have to reboot into Ubuntu and then I have no connection...

---

### Post by doctorbighands on 2008-09-14
Aha. Well, proceed with the CD, then!

---

### Post by OccamsShaver on 2008-09-14
Ok, I ran the package manager. Ndiswrapper was already installed (I did it yesterday when following that other tutorial), but I did install ndisgtk (or whatever it's called). When I went to System->Administration-> Windows Wireless drivers, it showed that the driver was already installed. When I clicked configure, everything was grayed out. I tried deleting the driver and then clicked to reinstall it. Same deal, I have no access to configure it. When I type lshw, it still shows as disabled.
Boy, this is fun! ;-o

---

### Post by doctorbighands on 2008-09-14
> **OccamsShaver said:**
> Ok, I ran the package manager. Ndiswrapper was already installed (I did it yesterday when following that other tutorial), but I did install ndisgtk (or whatever it's called). When I went to System->Administration-> Windows Wireless drivers, it showed that the driver was already installed. When I clicked configure, everything was grayed out. I tried deleting the driver and then clicked to reinstall it. Same deal, I have no access to configure it. When I type lshw, it still shows as disabled.
Boy, this is fun! ;-o

When you say you clicked configure, do you mean the Configure Network button? If so, in the window that pops up when you click that, there's a button at the bottom marked "Unlock." You need to click that to proceed with network configuration.

If you type "ndiswrapper -l" into the terminal, does it list an alternate driver? If so, what is it? The next step may be to blacklist the alternate driver.

---

### Post by SephirothLance on 2008-09-14
I'm having the exact same problem as Occam above, actually.  I have a broadcom draft-n wireless mini-card and I can't get ndiswrapper to load the driver for the life of me.  I've blacklisted the bcm43xx driver, the driver I've installed for the device is only available as part of a multi-device driver from Dell.  It's bcmwl6.inf.  It's installing properly through ndiswrapper, however, when I try and load it with depmod -a, then modprobe nidiswrapper it won't load the driver, all the relevant output I can think of is added below.  If anyone could assist me with this I'd greatly appreciate it. 

```
bcmwl6 : driver installed
	device (14E4:4328) present
xx@xx-laptop:~$ ndiswrapper -l
bcmwl6 : driver installed
	device (14E4:4328) present
xx@xx-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:d9:8c:d0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=xxx.xxx.xxx.xxx latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
xx@xx-laptop:~$ tail /var/log/messages
Sep 14 22:49:42 xx-xx kernel: [  118.768920] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Sep 14 22:49:42 xx-xx loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwl6 
Sep 14 22:49:42 xx-xx kernel: [  118.785399] usbcore: registered new interface driver ndiswrapper

```

If you notice in the lshw the wireless adapter is unclaimed, which I believe means there's no driver loaded for it.  I've read issues where people have said that they can't load the driver unless their wired connection is unplugged but I have the same issue either way.  Once again, I'd really appreciate any help.

---

### Post by OccamsShaver on 2008-09-15
> **doctorbighands said:**
> When you say you clicked configure, do you mean the Configure Network button? If so, in the window that pops up when you click that, there's a button at the bottom marked "Unlock." You need to click that to proceed with network configuration.

If you type "ndiswrapper -l" into the terminal, does it list an alternate driver? If so, what is it? The next step may be to blacklist the alternate driver.

"Unlock" is grayed out and there is no check mark next to "wireless connection". Ndiswrapper -l results in 
"device (14e4:4311) present (alternate driver: bcm43xx).

Also, my blacklist does contain the line "blacklist bcm43xx"

---

### Post by OccamsShaver on 2008-09-16
Bump

---

### Post by SephirothLance on 2008-09-19
[http://ubuntuforums.org/showthread.php?t=870086&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=870086&highlight=Broadcom)

Occam, try this wiki.  Just start all over from the beginning and ensure you have the proper windows driver for ndiswrapper to use.  This series worked for me, it's nothing I wasn't already doing I was just fortunate enough they had a different link for the driver I was trying to use that was actually supported (I could only find a vista driver, they offered an XP one.)  You might have more luck if you follow this one through.

---

### Post by OccamsShaver on 2008-09-19
Siphiroth - I'll try that...thanks for getting back to me. I'll post my results.

---

### Post by OccamsShaver on 2008-09-19
I followed the wiki to the letter, first trying step 2a (because I have rev. 01), then 2b. It looked like I connected to my wireless network, but it showed 0%, and of course I could not access any web pages. I know the router works (the same machine connects wirelessly when I boot to Win XP). It seems like it keeps deactivating the wireless card, requiring me to go back into the network menu and put the checkbox into "wireless" each time.  I also followed the steps to use ndiswrapper, to no avail.

What am I doing wrong here?

---

### Post by OccamsShaver on 2008-09-27
At last!!!
I left this alone for about a week. Then today, I uninstalled Ubuntu, reinstalled it, and followed that tutorial again...  now my wireless is working...thanks for all of the input!

---

