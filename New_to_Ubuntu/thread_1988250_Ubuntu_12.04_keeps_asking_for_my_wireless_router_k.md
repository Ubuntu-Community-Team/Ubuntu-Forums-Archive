---
title: "Ubuntu 12.04 keeps asking for my wireless router key"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by Drjim on 2012-05-27
Since i updated to Ubuntu 12.04, it keeps asking for my wireless router key in order to access wireless functions like internet access. I provide it and get access but keeps asking again every time I do something that uses wireless like starting Firefox or changing the webpage I'm on. 

If I don't provide the key each time, Ubuntu shuts down wireless access. The bottom line is that wireless is useless with the latest LTS distro.

Is there a fix for this or a way to go back to a previous distro?

Thanks,

Jim

---

### Post by mlentink on 2012-05-27
Could you tell us how you log in to ubuntu? Sometimes when you have set your system to log in automatically, it does not load your standard keyring and hence does not remember passwords and passphrases. 
Does your system 'forget' other passwords as well?

---

### Post by kurt18947 on 2012-05-27
> **Drjim said:**
> Since i updated to Ubuntu 12.04, it keeps asking for my wireless router key in order to access wireless functions like internet access. I provide it and get access but keeps asking again every time I do something that uses wireless like starting Firefox or changing the webpage I'm on. 

If I don't provide the key each time, Ubuntu shuts down wireless access. The bottom line is that wireless is useless with the latest LTS distro.

Is there a fix for this or a way to go back to a previous distro?

Thanks,

Jim

Which wifi device do you have?  If it's built into the machine like a laptop, could you open a terminal andpost the output of  <lspci>?.  If it's a USB device could you post the output of <lsusb>?  For example,  here is the output of my <lsusb>:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
**Bus 002 Device 002: ID 07d1:3303 D-Link System DWA-131 802.11n Wireless N Nano Adapter(rev.A1) [Realtek RTL8192SU]**
Bus 004 Device 002: ID 047d:2048 Kensington 
Bus 004 Device 003: ID 413c:1002 Dell Computer Corp. Keyboard Hub
Bus 001 Device 005: ID 04f9:01f3 Brother Industries, Ltd 
Bus 004 Device 004: ID 413c:2002 Dell Computer Corp. SK-8125 Keyboard

The bolded text tells us that the WiFi device uses a Realtek RTL8192SU chip which is what is helpful,  more than the manufacturer's model #

I had your problem with an RTL8188Cus device, being asked repeatedly for the WiFi key.  My problem was that the driver included in the default install worked .......sorta.  In my case the driver from RealTek fixed my problem.  That may not fix yours but knowing the chipset is a good first step.

---

### Post by johnneydarkness on 2012-08-28
I have a laptop with a Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01) which is doing the same thing right now. It was logging into my router at home w/o issues. It is now balking. I was just now able to "edit wireless settings" and it saved the password for real. The driver that I use (proprietary), Broadcom 802.11 Linux STA wireless driver, is Ubuntu certified.

---

### Post by kokoliko on 2012-11-27
First, the **fix** that worked for me:

Go into Network -> Wireless -> Options (for the wireless network you want to save the password for) -> Wireless Security (tab) -> Enter the password in the password field and press "SAVE".

(I find it silly that there isn't a "save password" checkbox in the regular wireless password prompt.)


My problem: 

I had the same problem with having to enter the wifi-password every time I logged in and also after using suspend mode (at least some of the times?).

I first tried to set the keyring password to "" (nothing) still having to input wireless password. I don't mind reducing the security like this since I don't save any passwords apart from the one for the wifi and that one is not crucial.

---

### Post by telegon on 2013-01-03
> **kokoliko said:**
> First, the **fix** that worked for me:

Go into Network -> Wireless -> Options (for the wireless network you want to save the password for) -> Wireless Security (tab) -> Enter the password in the password field and press "SAVE".

(I find it silly that there isn't a "save password" checkbox in the regular wireless password prompt.)


My problem: 

I had the same problem with having to enter the wifi-password every time I logged in and also after using suspend mode (at least some of the times?).

I first tried to set the keyring password to "" (nothing) still having to input wireless password. I don't mind reducing the security like this since I don't save any passwords apart from the one for the wifi and that one is not crucial.

This worked well for me and my Dell Latitude D630 after I applied [WildMan's Wireless NIC fix.]("http://ubuntuforums.org/showthread.php?t=2077104")

Thanks for your help!

---

