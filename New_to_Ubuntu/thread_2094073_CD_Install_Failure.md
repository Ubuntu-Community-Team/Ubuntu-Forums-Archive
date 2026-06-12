---
title: "CD Install Failure"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by fenquat on 2012-12-12
I have a Dell Inspiron that is semi dead- I get an error msg of unmountable boot volume. No back up discs that helped so I thought hmmmmm, I got an older laptop to work with a USB Puppy partioned install, let's go big time and completly change this one to Ubunto 12.10. It's specs are 1.50GHz, 2048MB and 400MHz memory and speed, 40gig hard drive of which about 30 were in use prior to it's demise
 
Disc in hand I changed so it boots from the CD, and fired it up. Up popped a screen titled XBOOT DVD with the options boot from Hard Drive, ubuntu for 32 bit and ubuntu for 64 bit. I toggled to 32 bit and got this:
 
GRUB4DOS 0.45b 2010-11-24, Mem: 636K/2038M/0M, End: 34d5a4
 
Reboot takes to the initial screen I described. Opting for the 64 bit gives the same message and opting the boot from hard drive takes me to the windows did not start, so sorry screen.
 
What are my current options?

---

### Post by GordThompson on 2012-12-12
Apparently there was a significant change in 12.10 that can prevent it from working on older platforms that do not support a technology called PAE. Can you try the same thing with 12.04 instead of 12.10?

---

### Post by fenquat on 2012-12-13
I made a 12.04 version onto a USB I had laying around and managed to get all loaded up. Seems to work ok, BUT, as I found from googleing around, like more than a few others I have no wireless.  The good news is it does work with a cable out of the router.
 
So spent the major portion of the morning reading this and trying that and I still have no wireless. 
 
In short, halfway there and the last half looks to be the hardest. Suggestions and solutions will be appreciated...

---

### Post by monkeybrain2012 on 2012-12-13
What is your wireless card?

Run 

```
lshw -C network
```

---

### Post by GordThompson on 2012-12-14
> **fenquat said:**
> So spent the major portion of the morning reading this and trying that and I still have no wireless.
Did you try this?

** System Settings > Hardware > Additional Drivers**

That got my wireless working on my Inspiron 1720.

---

### Post by fenquat on 2012-12-14
Monkeybrain, ran and got this:

 *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfbfe000-dfbfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:ce:20:8e:65
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-34-generic-pae firmware=N/A multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.




I can see it says DISABLED from peeking around on google and elsewhere it talks about a windows switch...not sure what that means but I can not access the windows part of this machine at all as the message I get when I attempt to boot is is unmountable boot volume. For what it is worth there is no physical switch to turn the wireless on or off either.

---

### Post by fenquat on 2012-12-14
Gord, I had tried that yesterday and got the message 'no proparitary driver are in use in this systems'

---

### Post by GordThompson on 2012-12-14
> **fenquat said:**
> Gord, I had tried that yesterday and got the message 'no proparitary driver are in use in this systems'
Mine said that too, but it also showed me a Broadcom driver that I could activate. Once I did that my wireless adapter started working.

---

### Post by fenquat on 2012-12-14
Gord, when I tried it previous the field of the box comes up empty, as it did today as well.




monkeybrain, I managed to get into settings and attempted to toggle the wireless to on, but after I saved and closed it made no difference.

I have a Belkin dongle that I will try to configure for a short term solution but as yet, no luck.

---

### Post by fenquat on 2012-12-14
...and the belkin works fine, that is what I an connected with currently, but as I said, short term solution ...

---

### Post by GordThompson on 2012-12-14
Okay, it looks like you're going to need to follow the guide [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access").

First step: Run the following command in a Terminal window and let us know what it says.

```
lspci -vvnn | grep 14e4
```

---

### Post by fenquat on 2012-12-14
ran it:

 buntu@ubuntu:~$ lspci -vvnn | grep 14e4

02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
ubuntu@ubuntu:~$ 





So if I am following things the Chip ID is BCM4318 and the PCI-ID is 14e4:4318 and the b43 open source is a match  and it looks to be supported.

So, is that indeed the one I should try to load in?

---

### Post by GordThompson on 2012-12-15
> **fenquat said:**
> So if I am following things the Chip ID is BCM4318 and the PCI-ID is 14e4:4318 and the b43 open source is a match  and it looks to be supported.

So, is that indeed the one I should try to load in?
Exactly! You already have the b43 driver, so once you've done...

```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```...and restarted your machine let us know how it went.

---

### Post by fenquat on 2012-12-15
Well how about that! 

The above and the balance of this note is being composed and more importantly sent with the cable disconnected and the internal wireless active and all that kind of good stuff.

Going to make some tweeks and tests on other functions and then completly convert this machine from windows to ubuntu-much thanks for the assistance supplied so far, most excellent.

Any suggestions on a good printed source or two on how best to use this new OS, tips, tricks and such? or any things to look out for when making the permanent load later today?

---

### Post by GordThompson on 2012-12-15
Congratulations! It sounds like you're in good shape.

The only other suggestion I can offer is that you might save yourself a bit of time when you do the re-install if you make sure you check the "Install this third-party software" checkbox as shown in the attached screenshot. The description does mention that it pertains to "some wireless hardware" and may copy the required files from the install DVD for you.

P.S. Remember to use "Thread Tools" at the top of this page to mark the issue [SOLVED].

---

