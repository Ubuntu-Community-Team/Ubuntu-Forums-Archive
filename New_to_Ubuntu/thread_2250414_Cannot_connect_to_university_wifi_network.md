---
title: "Cannot connect to university wifi network?"
date: 2014-10-28
forum: New to Ubuntu
---

### Post by Dan_L. on 2014-10-28
Hello, I have some issue connecting to my university wifi network. In fact, everytime I attemp to connect ot the wifi, it start to try to connect to it but eventually fail and saying You Are Now Offline (You know the grey text box on the right corner). Some time it wil try to reconnect but it will also fails. Here are some of the information about the wifi connection.  [B]


Authentication[/B]: WPA2 Enterprise
**Encryption**: AES
**802.1x/EAP type**: PEAP
**Authentication method**: MS-CHAP V2

However, my home wifi use WPA/WP2 Personal and it connects without any problem. 

Also, here are some information about my computer.

Device name: Acer Aspire One 722 (AMD version)
Memory: 3.6 GIB
Processor AMD C-50 Processor x2
Graphics: VESA: WRESTLER
OS type: 64-bit
Disk: 488.2GB
  
Ubuntu 14.01 LTS

I have an option in Additional Drivers in Software & Updates to check Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary) or check Do not use the device under Broadcom Corporation: BCM4313 802.11b/g/n Wireless LAN Controller 



I have tried both options in the wireless devices but they both give me the same results. 

Lastly, please do not ask me to consult the university IT department as thry provide no support for Linux. 

Thanks.

---

### Post by QIII on 2014-10-28
The issue is not your hardware or drivers if you can connect at home.

MS-CHAPv2 is a Microsoft-specific Challenge Handshake Authentication Protocol (extremely vulnerable and trivial to crack) that probably should not be used at all by anyone.  But if your University uses it you have to go with it.

The Virginia Tech Linux and Unix User Group may have an answer at [ https://vtluug.org/wiki/PEAP-MSCHAP]( https://vtluug.org/wiki/PEAP-MSCHAP) but I can't guarantee it will be useful to you.

---

