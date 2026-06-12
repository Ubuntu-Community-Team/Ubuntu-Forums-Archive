---
title: "Download fglrx?"
date: 2006-04-12
forum: Repositories &amp; Backports
---

### Post by nolongerlivecd on 2006-04-12
Hi guys, I'm stuck with a laptop that has Ubuntu installed, but cannot work in GUI mode, only Command Line. Reason being something to do with the driver. Is there anyway that I can install the driver/download it in Windows? My network has not been configured, using wired/wireless with Linksys WRT54G (i think), and it auto-assigns IP addresses. 

It always reports that "Failed to start X server"

Setup:
Acer Aspire 5504WXMi
Pentium M 760 2GHz
1GB DDR2 SDRAM
ATi Mobility Radeon X700 (cannot work with both vesa and vga) 64MB DDR SDRAM
Intel Centrino
Intel PRO/Wireless 2200BG
Some Broadcom Gigabit Ethernet (only using 100Mbps cable)
100GB Ultra/ATA 100 HDD (93GiB), out of which 87GiB Windows, 2GiB unallocated and last 6.1GiB Ubuntu
14.1" Widescreen with CrystalBrite/XBRITE/Ultrasharp/SuperFine WXGA 1280x800


So my questions are:

1) Is there a download for that I can use in Windows to set up my graphics card?
2) What could be causing the problem?
3) How do I set up the network connection?

---

### Post by kb3hkg on 2006-04-12
Yes you should be able to still download the driver from windows but you will have to be in linux to set it up. If you check through the forum you should be able to find links to download it.

As for your network connection, start with ifconfig, it is helpful to know what interfaces you already have recognized.

---

### Post by nolongerlivecd on 2006-04-12
I can only find the ATi version of the driver. However, when I try to run it in Ubuntu (I save it in a diff folder, on my Windows partition), it keeps giving me error messsages( cannot save files or something like that)

---

### Post by nolongerlivecd on 2006-04-12
After running ifcofig, I get:
eth0         Link encap:Ethernet HWaddr:(myMACaddress, won't reveal)
               BROADCAST MULTICAST MTU:1500 Metric:1
               RXpackets:0 errors:0 dropped:0 overruns:0 frame:0
               TXpackets:0 errors:0 dropped:0 overruns:0 carrier:0
               collisions:0 txqueuelen:1000
               RX bytes:0 (0.0 b)   TX bytes:0 (0.0 b)
               Interrupt:11

So how do I fix it?

---

### Post by kb3hkg on 2006-04-12
For the driver I recommend still getting it from the repositories, but download it in windows. That way you will have the right driver to install and it will work. Then just switch over to linux and install it.

For networking, try running dhcpcd and then ifconfig, see if it just isn't getting the ip address.

---

### Post by nolongerlivecd on 2006-04-12
Where do I download it?

---

### Post by nolongerlivecd on 2006-04-13
-bash: dhcpcd not found

---

### Post by nolongerlivecd on 2006-04-13
I've just run dhclient, got it to work, but cannot apt-get install xorg-driver-fglrx.

I can do "sudo apt-get upgrade", and it will tell me nothing to update. However, when I try the fglrx one, it doesn't work.

---

### Post by kb3hkg on 2006-04-13
What command are you trying and what does it say when you attempt to try it?

---

### Post by nolongerlivecd on 2006-04-14
Never mind, now I have the fglrx done, and I'm posting from my fresh Ubuntu 5.10.

However, how do I download and configure ipw2200? From the network configuration in the System->Administration, it says that it is well, working, active, but my internet connection becomes non-existent.

Also, why do I get an error message that my fglrx driver is outdated when I try to install the mirror.ubuntulinux.nl fglrx? It keeps telling me that my fglrx is outdated, and that I need fglrx-kernel.

When I try to install the ATi fglrx, it keeps telling me that Architecture not supported (generate distribution specifc package)

---

### Post by kb3hkg on 2006-04-14
Sorry but that I do not know. Hopefully someone else will come along and help you.

---

