---
title: "Need help with airodump"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by hellodoggie on 2008-08-07
Want to run 'sudo airodump eth1 airodumps channel#11'
but I am getting the error:

Unsupported hardware link type 803 - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead. Make sure RFMON is enabled:
run 'ifconfig eth1 up; iwconfig eth1 mode Monitor channel <#>'

We're using the ipw2200 driver for Intel Corporation PRO/Wireless 2200BG as our network controller and our Intel Corporation 82541GI Gigabit Ethernet Controller (the drivers work for one or both, we're not sure)  

Here are some relevant results from "lspci"

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
02:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 13)
02:01.0 Ethernet controller: Intel Corporation 82541GI Gigabit Ethernet Controller
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
matthew@matthew-laptop:~$ sudo lspci
[sudo] password for matthew: 
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
02:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 13)
02:01.0 Ethernet controller: Intel Corporation 82541GI Gigabit Ethernet Controller
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

Please Help
Thank you

---

### Post by cgkades on 2008-08-07
I have an intell card on my laptop that doesnt work with airodump. Check the compatibility list on aircrack-ng. You may need a different card (90% sure)

---

