---
title: "USB 3.0 Reaching Glacier speeds and CPU Sky rockets to 99%"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by shizz on 2012-03-07
No idea what was going on. I was transferring a 6GB file over USB 3.0 and it was quoting me over 3 hours to do it. At the same time the cpu usage hit the ceiling?

What could be causing this? Am I missing the drivers for USB 3.0?

I have checked the wiki for my laptop (Asus N53) and there's no reported issues there. 

Even in windows I don't seem to get the speeds that USB 3 should be getting. I havent checked what the root of this problem is, maybe bad driver or something, but the process took a few minutes. 

Please help me not use windows. :(

---

### Post by grahammechanical on 2012-03-07
Do you have the correct or the fastest setting for USB in the BIOS?

In my BIOS the lowest setting is equal to a floppy disk transfer speed. I think that it is for a USB connected floppy disk drive. 

I also note the Full Speed is 12Mbps, whereas High speed is 480Mbps. So, full speed is not the fastest setting. Strange that. This is for USB 2.0 which is what I have.

Regards.

---

### Post by HermanAB on 2012-03-07
Howdy,

There were schtoopidttt USB bugs a few months ago.  Ensure that you upgrade your system to the latest and greatest and the problem should go away.

---

### Post by NikTh on 2012-03-07
> **shizz said:**
> No idea what was going on. I was transferring a 6GB file over USB 3.0 and it was quoting me over 3 hours to do it. At the same time the cpu usage hit the ceiling?

Hi , if you want to see what causes the cpu overloading you can open a terminal and write ```
top
``` you will see then a list with applications that loading from you cpu. 

> **shizz said:**
> What could be causing this? Am I missing the drivers for USB 3.0?[/code]
At my USB 3.0 , had no need to install anything. Worked out of the box properly . 


Check your hardware first . Switch ports. I don't offend you with noob character , but i remember my self , so check that you have put your usb to correct port (blue one) and also to catch those (usb 3.0) speeds must flash disk (or ext.hdd) support USB3.0.

Check it from ubuntu. Plug your usb 3.0 disk and go to disk utility -> click your disk --> and you will see on the right of the window your disk's capable speed  480Mb/s for usb2.0 and 720Mb/s for usb 3.0 ( IF i remember correctly )

Thanks

---

### Post by shizz on 2012-03-08
Thanks guys I'll try your tips tonight when I get a chance. Much appreciated.

---

### Post by shizz on 2012-03-09
Hey guys, It was a friends usb 3 disk so I cant test it at the moment. I think I may have been missing the drivers for it in windows so I installed them.

As for the BIOS, there doesn't seem to be any option for me to see? It just says "support for legacy USB" or something like that, and I have it enabled.

---

### Post by Mark Phelps on 2012-03-12
I was not able to get decent USB 3.0 speeds and persistant connections until I upgraded BOTH the firmware and drivers -- for Win7 running on my Gigabyte motherboard.

Had to go to the Sony Renesas website and download both the the firmware update and driver update from them.

Did both updates in Win7 -- but once the firmware is updated, it should also work OK in Linux.  Don't know about the drivers, though.

---

### Post by shizz on 2012-03-12
> **Mark Phelps said:**
> I was not able to get decent USB 3.0 speeds and persistant connections until I upgraded BOTH the firmware and drivers -- for Win7 running on my Gigabyte motherboard.

Had to go to the Sony Renesas website and download both the the firmware update and driver update from them.

Did both updates in Win7 -- but once the firmware is updated, it should also work OK in Linux.  Don't know about the drivers, though.

I just tried it again, in windows, with the new drivers installed and the software that came with the hard drive. I was getting speeds of 12Mb/s on average. That is awful.

Should I update the BIOS?

---

