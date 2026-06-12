---
title: "Sound issues, please help"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by steveo862004 on 2008-07-07
Hi, i am vry new to linux, i just wiped my preconfigured desktop yesterday and loaded ubuntu hardy. I have never dealt with linux before and i am having a couple issues. the first one i would like to tackle is a problem with sound. I am running Wine to be able to run ventrilo(the linux version is still in development) and world of warcraft. I am still downloading wow but i was able to run Ventrilo last night using the windows version through Wine. The problem as that i couldn't  hear anybody talk, but i did see the mic light up so i knew they were talking, and i couldnt speak either, it wouldnt even que my mic. I think it has to due with a sound card driver problem.. since i havent installed one, but that is just a guess. the only programs i have installed other than ubuntu is Firestarter(which im having problems configuring), Ventrilo, Wine, and World of Warcraft. i am having trouble viewing HTML renderings (wow downloaders and open screen) and it has tryed to download gecko several ties without effect. Any help would be greatly appreciated. 

steven@steven-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)

any help is much appreciated.

---

### Post by ChameleonDave on 2008-07-08
Try doing a title search on these fora for "82801DB", or a Google search for "82801DB Linux" (without the quotation marks).

Try the documentation: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by joshsmith on 2008-07-08
install latest version of wine from here:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

as you may be having problems with the wine version in the repos not using pulse audio correctly

also check out the wine app db for that application to see if it is supposed to work

---

