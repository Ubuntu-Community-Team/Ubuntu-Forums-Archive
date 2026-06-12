---
title: "Ubuntu 12.04 Does NOT go ONLINE and see Video card"
date: 2013-07-14
forum: New to Ubuntu
---

### Post by MrStudent on 2013-07-14
[FONT=tahoma]The problem with Ubuntu for me is twofold.[/FONT]

[FONT=tahoma]The system is Dell - OptiPlex GX620
[/FONT]OS: Ubuntu 12.04 (64-bit)
Processor: Intel Pentium 4 CPU 2.80GHz
Motherboard: Dell - 0F8101

[FONT=tahoma]I can not access the USB wireless adapter even though I have tried for seeks.  The USB adapter is Linksys N300 Model No.: AE1200-NP.[/FONT]
[FONT=tahoma]I have tried to use Windows to upload drivers and place them in the partition Ubuntu is on.[/FONT]

[FONT=tahoma]The second problem is that Ubuntu never recognized the Sapphire video card.[/FONT]


I have even tried [http://www.driversdownloader.com/](http://www.driversdownloader.com/) to indirectly access Ubuntu but failed.


[FONT=tahoma]Please Help[/FONT]

---

### Post by claracc on 2013-07-14
About your usb adapter, it seems there is compatibility problems with this hardware and linux.

I have found this link, [http://askubuntu.com/questions/100090/how-do-i-install-the-driver-for-my-linksys-ae1200-wireless-n-usb-adapter](http://askubuntu.com/questions/100090/how-do-i-install-the-driver-for-my-linksys-ae1200-wireless-n-usb-adapter) , where there are some approaches to the problem, which are reported as working.

Your better bet seems to be using ndiswrapper

---

### Post by 3rdalbum on 2013-07-14
Sapphire makes ATI graphics cards. Assuming this card is the same vintage as the rest of the computer, ATI dropped support for it years ago. The drivers Ubuntu is using are the only ones available.

One of the latest ATI cards, or even better a recent Nvidia card, would be a great investment.

---

