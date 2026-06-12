---
title: "No Valid Connections"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by raxhunter on 2012-02-22
Hello all,

First I would like to thank every one who helped me get my server up and running with UBUNTU GUI.
Now comes my second question :P I am currently running UBUNTU 11.10 with the GUI. I am wanting to use my server to serve media such as pictures music and home movies with mostly family and friends. I have done some research and it should be fairly easy to set up, but my UBUNTU sez I dont have a connection.  I go to connection information and I get this error "No valid active connections found!" my server is wired into my Cisco router. I understand that i need to be able to look at my connection info to get my server to do what I would like it to do... I know I have a connection as I am posting this from my server. 

Any Ideas?

---

### Post by raxhunter on 2012-02-22
Okay I did some more research and reading. I installed WICD, but i get this error" Failed to run /usr/sbin/wicd as user root. Wrong password". I only have one password on this server, and for some reason it dont work, du I need to set up WICD as a root user? with its own password? if so or if not I am stumped......

---

### Post by raxhunter on 2012-02-22
Im starting to think that linux may not be for me as its complicated.

---

### Post by 3rdalbum on 2012-02-22
Wicd is only for wireless so don't worry about it.


Instead of going to Connection Information, can you just go to the network indicator on the top panel and left click, and tell us what you see? A wired connection should already be active. Ubuntu is pretty automatic with this stuff but you might just need to click on your wired connection in the network indicator.

---

### Post by raxhunter on 2012-02-22
when I right click a drop down menu appears.   In a gray color it sez "Wired Network device not managed", VPN connections are in whits and am able to click on it, a check mark is by enable networking and I am able to click on that also, connection information and am able to click on that one and edit connections and am able to click on that one also.

---

### Post by 3rdalbum on 2012-02-22
> **raxhunter said:**
> when I right click a drop down menu appears.   In a gray color it sez "Wired Network device not managed", VPN connections are in whits and am able to click on it, a check mark is by enable networking and I am able to click on that also, connection information and am able to click on that one and edit connections and am able to click on that one also.

Well, that's something I've never seen before. Maybe if you use Google to search for the chipset number of the network card and the word Ubuntu? Somebody may have previously overcome whatever this problem is.

You can find the chipset number of the network card by putting "lspci" into the terminal. (that's a lowercase LSPCI).

---

### Post by raxhunter on 2012-02-23
Thanks, Ill give that a try..

---

### Post by raxhunter on 2012-02-23
Ill C&P the lspci info

---

### Post by raxhunter on 2012-02-23
robert@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation E7520 Memory Controller Hub (rev 09)
00:02.0 PCI bridge: Intel Corporation E7525/E7520/E7320 PCI Express Port A (rev 09)
00:04.0 PCI bridge: Intel Corporation E7525/E7520 PCI Express Port B (rev 09)
00:06.0 PCI bridge: Intel Corporation E7520 PCI Express Port C (rev 09)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
01:00.0 PCI bridge: Intel Corporation 6700PXH PCI Express-to-PCI Bridge A (rev 09)
01:00.2 PCI bridge: Intel Corporation 6700PXH PCI Express-to-PCI Bridge B (rev 09)
02:04.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 08)
[COLOR=Red]03:07.0 Ethernet controller: Intel Corporation 82541GI Gigabit Ethernet Controller (rev 05)[/COLOR]
03:09.0 RAID bus controller: Adaptec AAC-RAID (rev 01)
06:03.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)
06:05.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
robert@ubuntu:~$ 

I done a search using google, of the red highlighted color and UBUNTU, but am unsure if there is an update and how to get the update if needed.  Its wierd as I said before I am using my server to post this stuff... I would think if my adapter wasnt working I wouldnt have internet on this station.

---

