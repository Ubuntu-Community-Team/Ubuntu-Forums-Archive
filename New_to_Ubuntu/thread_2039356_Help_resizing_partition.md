---
title: "Help resizing partition"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by docpat2511 on 2012-08-08
Hello, all.

I am entirely new to Linux. I installed Ubuntu (latest version) in a dual-boot configuration with Windows XP off a USB stick (not WUBI).

Everything was going swimmingly until I tried syncing my (large) Dropbox account. Ubuntu ran out of disk space and I realized I made the noob mistake of setting Ubuntu's size to 16gb. I need more like 100 to be safe.

I have read instructions on how to resize partitions but none of them seem to quite apply to my situation, and I do not want to lose a day monkeying with a scrapped hard drive. I need some hand-holding. I have read it is possible for some resizing methods to remove the Linux bootloader and leave the computer unbootable. I have seen instructions for using gparted to resize partitions, but if I do so, do I risk that problem?

Thanks.

---

### Post by paichkash on 2012-08-08
ahhhh very sad to know taht .. its something which i encountered and learned the hard way..


never ever perform any disk checking or resizing opperations while its mounted..

second thing.. get a live cd of ubuntu .. and then start gparted then u can easily resize it .. i have done so without any loss of any data...

i would strongly recomend u to first post the image from the gparted screen here .. do not proceede now.. first let me/and others see that and we will recomend u..

:guitar:

---

### Post by Bashing-om on 2012-08-08
Guys, Just a reminder .. it is recommended to mess with micro$oft partitions with the micro$oft tools....and then apply Gparted.
       and hey ... we will get you through this

---

### Post by docpat2511 on 2012-08-09
Thanks, guys.

I need to back up everything before I start messing with anything. I'll try to do that and burn the boot CD tomorrow.

What are the Windows tools for partition management?

~Pat.

---

### Post by paichkash on 2012-08-09
windows default tools are in adminstrative tasks in control panel .. that is very basic tool and is dangrous..

commercial tools are
partition magic 8.30 (if u are only using upto xp.. dont use it if u are using anything above)

minitools..

and some which i dont remember now u can google for them ..

---

### Post by paichkash on 2012-08-09
Acronis Disk Director
EASEUS Partition Master
Paragon Partition Manager
 dont use any othe tool except these few..
these may have a trial or home version for free search them.. and use with caution..

when moving data it takes tremendous time ..

---

### Post by docpat2511 on 2012-08-09
Thanks.

I've been loaded with work so haven't had time to do more than finish my backups. I use Acronis products for several other tasks so probably will try them first.

I'll be back when I have some time to do this safely.

Thanks again, everybody.

---

### Post by Fluteamahoot on 2012-08-09
Word of advice, always have a couple live cd/usb around. I personally use the #! live cd and heron Boot CD. both are fast and full-featured.

---

### Post by docpat2511 on 2012-08-09
Got it done with Acronis and a little help from my friends!

Thanks, guys.

~Pat.

---

