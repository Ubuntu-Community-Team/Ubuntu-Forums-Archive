---
title: "Remove Win8.1, install Ubuntu?"
date: 2013-12-25
forum: New to Ubuntu
---

### Post by brunswick.b.r.g on 2013-12-25
.....or can she?

Greetings to all at ubuntuforums,

I was wondering what my chances are of installing ubuntu onto this POS system that I currently use. I'm guessing that some sort of bios flash/chipset update may be the order of the day but I have been unable to find any bios downloads on the HP site and had no luck when I enquired on the MSI forum either. 

Motherboard      MSI 2AE0  rev 1.0
Chipset             AMD A55/A60M/A88 FCH  rev 0.0
Southbridge      AMD A55/A0M  rev 11
Bios                  AMI version 8.07 (jasmine)
LPCIO               Fintek F71808A
CPU                  AMD A4-5300 (Trinity - socket FM2)
GPU on-board    AMD Radeon HD 7480D

Skillfully concealed inside a HP Pavilion p6 2310ea, currently running Windoze 8.1


Thanks for reading, look forward to your replies.

---

### Post by overdrank on 2013-12-25
> **brunswick.b.r.g said:**
> .....or can she?

Greetings to all at ubuntuforums,

I was wondering what my chances are of installing ubuntu onto this POS system that I currently use. I'm guessing that some sort of bios flash/chipset update may be the order of the day but I have been unable to find any bios downloads on the HP site and had no luck when I enquired on the MSI forum either. 

Motherboard      MSI 2AE0  rev 1.0
Chipset             AMD A55/A60M/A88 FCH  rev 0.0
Southbridge      AMD A55/A0M  rev 11
Bios                  AMI version 8.07 (jasmine)
LPCIO               Fintek F71808A
CPU                  AMD A4-5300 (Trinity - socket FM2)
GPU on-board    AMD Radeon HD 7480D

Skillfully concealed inside a HP Pavilion p6 2310ea, currently running Windoze 8.1


Thanks for reading, look forward to your replies.

Hi and welcome, have no idea why you would call that system a POS but I think it would run Ubuntu fine.

---

### Post by brunswick.b.r.g on 2013-12-25
Thanks for the welcome. Maybe the OS is tainting my view of the system.

Either way, are you saying that I can install ubuntu onto this system without the need for a chipset update or a bios flash?

---

### Post by steeldriver on 2013-12-25
Have a look at the [minimum system requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements") - provided your system satisfies those (especially the minimum RAM) you should be good to go - the main issues people have beyond minimum requirements are with things like graphics and wifi devices where manufacturer support for Linux is sometimes lacking

Really the best thing would be to burn a DVD / USB and try it in 'live' mode before installing to make sure that everything works.

---

### Post by brunswick.b.r.g on 2013-12-25
System requirements are fine, got 8gb of ram. 

Have been doing a bit of research, do I need to disable fast boot and UEFI to boot ubuntu from a usb or is that old news?

---

### Post by tgalati4 on 2013-12-25
Reminds me of a Christmas Story.  I met James [Doohan]("http://en.wikipedia.org/wiki/James_Doohan") (Star Trek's Scotty) in 1988 at a Christmas Boat Parade.  He was a guest on David Foster's boat, which I was helping to decorate for the parade. He loved to tell stories.

Anyway, your system will run Linux fine.  

Merry Christmas Everyone!

---

### Post by brunswick.b.r.g on 2013-12-25
Yeah, got that. The system is ok for ubuntu.

Still not sure if I am going to have any fast boot/UEFI problems after installing ubuntu though.

---

### Post by grahammechanical on 2013-12-25
Ubuntu can cope with UEFI and since Ubuntu 12.10 can also install on a motherboard with Secure boot enabled. But I have read that fastboot must most definitely be off. Here is where I read it.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

There are other tricks needed to get Ubuntu living side by side with Windows 8. My advice? Read some of the forums posts about installing on a machine with Windows 8 and see what can go wrong and what you can do about it.

> 
[LIST]
[*=left][FONT=inherit]In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").[/FONT]
[/LIST]

Regards.

---

### Post by brunswick.b.r.g on 2013-12-25
Thanks for all the advice.

Sorry for not being clearer in the OP, I am intending on removing win8.1 completely and just using ubuntu, if all goes well with my 'live mode' trial. 

I guess I still need to disable the options mentioned above ?

---

### Post by oldos2er on 2013-12-25
While I'm a huge Star Trek fan, this is a technical support forum so I've changed your thread title to reflect your question.

---

