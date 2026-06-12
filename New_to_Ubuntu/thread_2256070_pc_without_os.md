---
title: "pc without os"
date: 2014-12-09
forum: New to Ubuntu
---

### Post by Allisterguy on 2014-12-09
Hi
I am being given a  new packard bell pc which has no operating system.
I want to install ubuntu ( I have had unbut 12 on an old computer and really like it.)
 my question is will I need anything for the installation of Ubuntu ?
 I would assume the bios system works. 
What would be the best way to unstall Ubuntu
any advice appreciated.
Ps i am a novice.

---

### Post by sudodus on 2014-12-09
Welcome to the Ubuntu Forums :-)

Please tell us about the specification of the computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

or at least give us a hint of the age and kind of computer. The advice will depend a lot on what kind of computer it is.

---

### Post by Allisterguy on 2014-12-09
hi
Santa is bringing it so its new, here are details:-
Packar bell S2185
Processor AMD E1-2500
(14 ghz. 1MB cache)
Ram 4 GB DDR3
Storage 500 GB, 7200 rpm
Optical dr DVD/RW
Wireless NO
Bluetooth 4.
USN 3.0 X 2
USB 2.0 X 6

I have several old computers (windows 7) that could be available for spare parts if they were compatable.
Thanks for your quick response

---

### Post by sudodus on 2014-12-09
I would suggest that you download the iso file of ***Xubuntu 14.04.1 LTS 64-bit*** and try it live before installing. Boot from a USB drive. Make it bootable as described in this link (and links from it)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

See also the following link

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by sammiev on 2014-12-09
You have enough horses under the hood to run any of the 14.04 LTS versions. Try them all from a USB live stick and pick what works for you.

---

### Post by kansasnoob on 2014-12-09
> **sammiev said:**
> You have enough horses under the hood to run any of the 14.04 LTS versions. Try them all from a USB live stick and pick what works for you.

+1!

---

### Post by ajgreeny on 2014-12-09
If you were using Ubuntu 12.04 or 12.10 on an older machine, and liked the unity desktop, ie the one with the launchbar of icons down the left hand edge, you will love Ubuntu 14.04 with unity; it is much smoother and a bit more configurable than 12.04 was in my opinion, and with that configuration of machine it should work fine.

Watch out for the UEFI (the update to the legacy BIOS) which can catch you out if you are not careful.
All details of that can be read about at [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI")

---

### Post by mastablasta on 2014-12-10
you will want AMD drivers for the APU. use additional drivers utility to install them. And use 14.04 at least or 12.04 but make sure it's with later kernel.

---

### Post by Allisterguy on 2014-12-13
Thanks for all the replies and advice.
I got the new computer and although it said no wireless I popped a ubuntu 14.10 disc in and installed it on trial mode. it worked ,  there seemed to be no problems.
On my old computer when I installed 10.14  it would not download any software. It said "could not access repositories, check internet connection" yet i had no problem with getting mail and using firefox. I tried installing Mint and this worked ok no downloading problems. dont know why unbutu would not download, I reinstalled it several times. peculiar.
On the new computer i downloaded vlc  and several othe programs with no problem so I then asked it to install ubuntu selecting the default instal. Works great.
Dont understand the no wireless. is wireless and wifi different? I am pluged into an ethernet adaptor in the mains electricity.
Love 14 10.
Thanks again for the advice.
Allister

---

### Post by sudodus on 2014-12-13
> **Allisterguy said:**
> Thanks for all the replies and advice.
I got the new computer and although it said no wireless I popped a ubuntu 14.10 disc in and installed it on trial mode. it worked ,  there seemed to be no problems.
On my old computer when I installed 10.14  it would not download any software. It said "could not access repositories, check internet connection" yet i had no problem with getting mail and using firefox. I tried installing Mint and this worked ok no downloading problems. dont know why unbutu would not download, I reinstalled it several times. peculiar.

If you could get mail and use firefox, your internet connection was OK.

Maybe there was a temporary error with Ubuntu's server, so that the repositories were not available.
Maybe there is some problem with a driver for some hardware, that is not working properly, and causes problems with the old computer. It might work better with an older version 12.04.5 LTS or 14.04.1 LTS (while there are problems with 14.10) in that computer.
> 
On the new computer i downloaded vlc  and several othe programs with no problem so I then asked it to install ubuntu selecting the default instal. Works great.
Dont understand the no wireless. is wireless and wifi different? I am pluged into an ethernet adaptor in the mains electricity.
Love 14 10.
Thanks again for the advice.
Allister

At least for me, wifi and wireless LAN mean the same. Ethernet adaptor in the mains electricity means 'home plug' to me, and for the computer it behaves like normal wired connection (ethernet).

---

### Post by buzzingrobot on 2014-12-13
You won't have wireless/wifi unless the machine has a wireless/wifi chip or card.  Not really a loss in an ethernet-connected desktop since you don't carry the desktop around and ethernet is very often faster than wifi.

---

