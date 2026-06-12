---
title: "Asus X501A - Cannot install Ubuntu"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by CraigD92 on 2013-01-20
Hi guys,

I'm attempting to install Ubuntu on my Windows 8 laptop. I successfully dual booted Ubuntu with Windows 7 in the past, but I've done a clean install of Windows 8 recently and, as it's a usability nightmare (IMO) I'm looking to either dual boot Ubuntu, or wipe out Windows 8 completely and install Ubuntu.

I've tried booting from both a Live USB and CD and changed the boot order in BIOS. However, it always boots straight into Windows 8. I'm pretty sure that it has a UEFI boot manager, so I'm not sure if that is causing problems. 

Does anyone else have any insight on what might be preventing me from booting into Ubuntu 12.04? And how might I go about getting it to boot into Ubuntu successfully? Or how could I wipe Windows 8 from the system? 

Thanks for any help.

---

### Post by mapes12 on 2013-01-20
> Or how could I wipe Windows 8 from the system? [Killdisk]("http://how-to-erase-hard-drive.com/")

---

### Post by ajgreeny on 2013-01-20
It will probably be the UEFI that is your downfall at the moment.  You will need to go into the BIOS and disable secure boot, or whatever it's called.

I do not know more about this than you can find at 
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
or any of the other results shown at
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=uefi+secure+boot&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=uefi+secure+boot&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by CraigD92 on 2013-01-22
Hi guys, 
I must have made the live USB incorrectly because after making another one it boots into Ubuntu.

My problem now is that I cannot get Wifi to work with the Live USB?
Can anyone help?

---

### Post by Cheesemill on 2013-01-22
It should just work. I installed 12.10 on my Asus X501A about 5 months ago and everything worked out of the box, no extra drivers were needed.

I'm not with the laptop at the minute but next time I am I'll double check what wireless hardware it has. In the meantime try connecting using a network cable and going to Software Sources > Additional Drivers and seeing if it recommends anything.

---

