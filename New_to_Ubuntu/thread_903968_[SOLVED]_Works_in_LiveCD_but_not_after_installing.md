---
title: "[SOLVED] Works in LiveCD but not after installing"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by motang on 2008-08-28
Hello, I installed Kubuntu 8.04.1 Remix and wipped that and installed Kubuntu 8.04.1 LTS as I thought it was KDE 4.1.  But it's seems that the SD card reader works fine in Live CD without any problmes, but when I install the OS on to the hard drive no luck.  I typed in *dmesg | tail* and I get this message:
> [ 2909.507676] ISOFS: Unable to identify CD-ROM format.
[ 2916.680497] UDF-fs: No VRS found
[ 2916.769086] ISOFS: Unable to identify CD-ROM format.

Any suggestions on how I can fix this?  Thanks in advance.

Oh, BTW I am running all of this on the Asus EEE Box.

---

### Post by Crafty Kisses on 2008-08-28
What are your system specs?

---

### Post by motang on 2008-08-28
> Name and Model: Eee Box B202
OS: Linux System / Hardware Compatible with Windows XP
Processor: Intel Atom N270 (1.6 GHz, FSB 533)
Memory: DDRII 1 GB
Storage: 80 GB
Chipset: 945GSE + ICH7M
VGA: On-board Intel GMA 950, 1600 x 1200 maximum resolution
Networking: 10/100/1000 Mbps LAN, 802.11n WLAN, Bluetooth optional
SD/MMC/MS slot: SD, SDHC, Mini SD, (Micro SD through adapter) ; MMC, MMC plus, MMC4.x, RS MMC, RSMMC4.x (MMC mobile through adapter);MS,MS PRO
Audio: Azalia ALC888 Audio Chip

source: [http://www.hothardware.com/News/ASUS_Eee_Box_B202_Details_Emerge/]("http://www.hothardware.com/News/ASUS_Eee_Box_B202_Details_Emerge/")

---

### Post by motang on 2008-08-31
Fixed the issue, in fstab it was point to the SD Reader as a CD-Rom drive so I commented that line out and afterwards I was about to mount and view/edit the content on the SD Card.

---

