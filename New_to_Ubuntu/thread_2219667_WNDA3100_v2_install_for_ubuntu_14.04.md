---
title: "WNDA3100 v2 install for ubuntu 14.04"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by Oscar_Gardea on 2014-04-25
Hello everybody, Im new to ubuntu and have been trying to install the drivers for my wnda3100 v2 usb, with no success, I have currently read forum [http://ubuntuforums.org/showthread.php?t=1964173&highlight=netgear+wnda3100](http://ubuntuforums.org/showthread.php?t=1964173&highlight=netgear+wnda3100) and im stuck on point step 10, everytime i try to do the following command:
[COLOR=#000000][FONT=Ubuntu Mono]
sudo ndiswrapper i- bcmn43xx64.inf ( i used the 64 as my cpu and version of ubuntu are the 64 bit) 

the message i get states that 


[/FONT][/COLOR]oscar@Toby:~$ sudo ndiswrapper -i bcmn43xx64.infcouldn't open bcmn43xx64.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 162.

I also tried the [4bit_v3.tar.gz]("http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz") through the same command ( i got that file from [http://ubuntuforums.org/showthread.php?t=2218375](http://ubuntuforums.org/showthread.php?t=2218375)) and same results.

Ive been able to do the other prior commands for both forums, and have downloaded ndiswrapper

Any help is appreciated

---

