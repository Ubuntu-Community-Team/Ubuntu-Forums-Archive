---
title: "So far so good"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by intrepid1960 on 2013-05-02
I attempted to install Ubuntu along side Windows.  The result was ugly. It killed my MBR and GRUB just failed miserably.  So after a long search of my house for and the failure to locate my master Windows disk, i decided to install Ubuntu fresh.  Erased the C drive and just started over.  Had another windows machine(wifes) in the house and had all my files backed up.  So wan't too concerned.

My initial evaluation after 1 week.  I like it.  So are the only issues I have are:

1. No Neat Scanner support. (Just moved it too my wife's windows machine)
2. Can't get my Neat Gear WPN311 Wireless card to work.  (Using a WiFi thumb drive I bought for my Raspberry PI)
3. My "RealFlight" R/C simulator doesn't run on Ubuntu. (Moving it over to my wife's windows machine.

Couple of questions that I could use help with:
1. During my effort to setup a dual boot machine I setup a 79gb partition on an external 2TB drive.  How do I kill the partition and add it back to the rest of the drive?
2. Any suggestions on my WPN311 issue?

Mike

---

### Post by papibe on 2013-05-02
> **intrepid1960 said:**
> How do I kill the partition and add it back to the rest of the drive?
Hi intrepid1960. Welcome to the forum ):P

Install 'Gnome Partition Editor' (gparted). Carefully select the external disk (you'll know by its size), delete the partition you want, and then take the other remaining partition and increase its size to take advantage of the unused space you just freed.

Hope it helps. Let us know how if you need more help with that.
Regards.

---

### Post by intrepid1960 on 2013-05-02
Thanks, I will give that a try.

---

### Post by intrepid1960 on 2013-05-02
BTW, what about AntiVirus and Spam tools? Is it an issue with Ubuntu? Any suggestions?

---

### Post by alhefner on 2013-05-02
> **intrepid1960 said:**
> BTW, what about AntiVirus and Spam tools? Is it an issue with Ubuntu? Any suggestions?

What, you don't like Spam? :lolflag: I think Thunderbird mail client has a good spam filter you can use. I don't have any suggestions for anti-malware though... seems to not be a big issue with Linux... I could very well be wrong.

---

### Post by BluNova on 2013-05-02
> **intrepid1960 said:**
> I attempted to install Ubuntu along side Windows.  The result was ugly. It killed my MBR and GRUB just failed miserably.  So after a long search of my house for and the failure to locate my master Windows disk, i decided to install Ubuntu fresh.  Erased the C drive and just started over.  Had another windows machine(wifes) in the house and had all my files backed up.  So wan't too concerned.

My initial evaluation after 1 week.  I like it.  So are the only issues I have are:

1. No Neat Scanner support. (Just moved it too my wife's windows machine)
2. Can't get my Neat Gear WPN311 Wireless card to work.  (Using a WiFi thumb drive I bought for my Raspberry PI)
3. My "RealFlight" R/C simulator doesn't run on Ubuntu. (Moving it over to my wife's windows machine.

Couple of questions that I could use help with:
1. During my effort to setup a dual boot machine I setup a 79gb partition on an external 2TB drive.  How do I kill the partition and add it back to the rest of the drive?
2. Any suggestions on my WPN311 issue?

Mike
1) I don't know what that is
2) Please post the results of the commands **lsusb **Open it in the program called terminal
3) It's windows only sorry, there's no way around that

---

### Post by intrepid1960 on 2013-05-02
Bus 002 Device 002: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 002 Device 003: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 002 Device 004: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 004 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 08ca:0010 Aiptek International, Inc. Tablet
Bus 002 Device 006: ID 0bc2:5071 Seagate RSS LLC 
Bus 002 Device 007: ID 0bc2:3008 Seagate RSS LLC 
Bus 002 Device 008: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 002 Device 009: ID 045e:0728 Microsoft Corp.

---

### Post by AndyOpie150 on 2013-05-03
For help with your wireless adapter card go to the "Networking and Wireless" forum.

---

