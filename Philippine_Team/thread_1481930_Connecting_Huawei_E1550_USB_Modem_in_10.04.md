---
title: "Connecting Huawei E1550 USB Modem in 10.04"
date: 2010-05-13
forum: Philippine Team
---

### Post by killer_d76 on 2010-05-13
First time I installed 10.04 on our lappie is that I found surprisingly fast!.. but I had an issue getting my Huawei USB Modem E1550 be detected! then I tried installin "usb mode switch" and Voila! my modem is now detected!.. though I still need to configure the VPN for it to work properly though ;)

---

### Post by outkast08 on 2010-05-15
I also had the same problem, I haven't tried that "usb mode switch" I was not able to install it because I did not have an Internet connection.
But I was able to solve my problem using this guide:


[[COLOR="Blue"]**Huawei E1550 on Ubuntu**[/COLOR]]("http://blog.lynxworks.eu/20090830/huawei-e1550-on-ubuntu")

[[COLOR="Blue"]**Huawei E1550 on Ubuntu 10.04 Lucid Lynx**[/COLOR]]("http://franklinchua.wordpress.com/2010/05/03/huawei-e1550-on-ubuntu-10-04-lucid-lynx/")

I just had to create a file, after that my USB modem was detected.

---

### Post by killer_d76 on 2010-05-15
I tried what was instructed on the links that you have provided the first time I installed 10.04 but what happened was all my USB storage devices were not detected by my laptop!.. so I re-installed 10.04 played installed usb-switch-mode and it works for me!... though thanks for the links anyway perhaps other 10.04 user using Huawei E1550 may help this thread! ;)

---

### Post by EIxIO on 2010-05-16
yes. perfectly. it helps. hehe popost ko palang tanong. sagot na. thanks hehe XD

---

### Post by outkast08 on 2010-05-17
> **killer_d76 said:**
> I tried what was instructed on the links that you have provided the first time I installed 10.04 but what happened was all my USB storage devices were not detected by my laptop!.. so I re-installed 10.04 played installed usb-switch-mode and it works for me!... though thanks for the links anyway perhaps other 10.04 user using Huawei E1550 may help this thread! ;)

Thanks for the info, I haven't tried using other USB devices yet other than the USB Huawei E1150 modem #-o. I'll try my other USB devices when I get home later. I'll just install usb-switch-mode if the other USB devices are not detected. This will be easy now that I have an internet connection, the E1150 is my only tool right now when connecting from home :).

---

### Post by outkast08 on 2010-05-17
**killer_d76** you were right, my external hard disk was not detected. I installed "usb mode switch" then removed the **15-huawei-155x.rules** file that i created in the **/etc/udev/rules.d**. Now I can use the usb modem and the usb storage....:)

---

### Post by echo2knight on 2010-05-17
Hey guys... I know this is OT... But can you help me as to how to prevent lynx from mounting the CD storage of the e1550 modem... since we will not be using this under linux...

thanks for the help in advance.

---

### Post by Ravskie on 2010-05-17
> **echo2knight said:**
> Hey guys... I know this is OT... But can you help me as to how to prevent lynx from mounting the CD storage of the e1550 modem... since we will not be using this under linux...

thanks for the help in advance.


na install mo na po ba usb-modeswitch ?  

in that way it will read as usb modem not CD storage .....

---

### Post by echo2knight on 2010-05-18
> **Ravskie said:**
> na install mo na po ba usb-modeswitch ?  

in that way it will read as usb modem not CD storage .....


@Ravskie: Thanks for the reply, and yes it is installed in my system.

I can use the modem, however, it still mounts the cd storage. Like I said before, the cd storage will not be needed as it is a windows application.

Any way to prevent the system from automunting the cd storage.

As always, many thanks in advance to all ubuntites.

---

### Post by aljoriz on 2010-05-18
You need a software in windows parang QPST something then you delete the cd iso.  Maganda nga mag delete ng iso eh para pag may humiram ng usb modem mo useless sa kanila yan :)

---

