---
title: "Missing Firmware for netbook wireless card"
date: 2012-07-31
forum: New to Ubuntu
---

### Post by Blkbuddha on 2012-07-31
I have read some of the posts and still have no idea of what to do or where to go. I am completely new to Linux and the Ubuntu software.

I have a Compaq net book that I received from Verizon when I signed up for Fios. I have decided to play around with Ubuntu on it. I installed the net book version which is 10.4 I believe and now the wireless card is not working. I do not have the ability of plugging the net book into the modem as it resides inside my landlords house and I do not have accesses to it. I wanted to download the proper firmware but where do I go and how do I install it once I get it.  Any links anybody can provide to help will be much appreciated. 

Recap Questions:

1: A link to the firmware for the Broadcom 4312 802.11b/g (Demi-2) WLAN adapter for download

2: A link of how to install the firmware by usb stick

Thank you anybody that can help hope to get this up and running soon been at this for a couple of days now and its driving me mad.

---

### Post by Kelvari on 2012-07-31
Personally, I would recommend connecting to a wired connection, but I believe the package that you'll be looking for will be b43-fwcutter

[http://packages.ubuntu.com/precise/b43-fwcutter](http://packages.ubuntu.com/precise/b43-fwcutter)

---

### Post by wildmanne39 on 2012-07-31
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by bkratz on 2012-07-31
> **Blkbuddha said:**
> I have read some of the posts and still have no idea of what to do or where to go. I am completely new to Linux and the Ubuntu software.

I have a Compaq net book that I received from Verizon when I signed up for Fios. I have decided to play around with Ubuntu on it. I installed the net book version which is 10.4 I believe and now the wireless card is not working. I do not have the ability of plugging the net book into the modem as it resides inside my landlords house and I do not have accesses to it. I wanted to download the proper firmware but where do I go and how do I install it once I get it.  Any links anybody can provide to help will be much appreciated. 

Recap Questions:

1: A link to the firmware for the Broadcom 4312 802.11b/g (Demi-2) WLAN adapter for download

2: A link of how to install the firmware by usb stick

Thank you anybody that can help hope to get this up and running soon been at this for a couple of days now and its driving me mad.



Try this link for the b43 driver

[http://ubuntuforums.org/showpost.php?p=11860231&postcount=8](http://ubuntuforums.org/showpost.php?p=11860231&postcount=8)

---

