---
title: "reformat disk"
date: 2013-02-20
forum: New to Ubuntu
---

### Post by groe on 2013-02-20
I have a hard disk so thoroughly screwed up that it won't accept an installation of 11.10. I'd like to wipe the disk clean and format it so that it will accept it, but the tools provided are unintelligible to me. I don't understand which format to select, what start and end points are, etc. Any suggestions appreciated. Thanks.

---

### Post by The Cog on 2013-02-20
You shouldn't need to know how to use those tools. The installer should offer you an option to erase the disk as part of the install. If that fails then all I can suggest is wiping the boot sector and starting again. 

If you feel this is necessary, AND the hard disk is the only one in the computer, then this command should wipe it. 
DO NOT use this command if there is anything in the computer that you want to keep:
```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```

So if the computer contains more than 1 hard disk, please post the output of this command and seek further advice (that last character is a lower-case 'L'):```
sudo fdisk -l
```

---

### Post by Impavidus on 2013-02-20
Also, do you have a special reason to install 11.10? If you do, that's fine with me, but 11.10 is almost end of live. Consider installing 12.04 instead.

---

### Post by groe on 2013-02-21
Thank you both. I tried the solution given, but installation failed. I guess it could be a hardware problem. I needed a new doorstop anyway, so I'll install 12.04 on another machine.

---

### Post by deadflowr on 2013-02-21
Do you anything about the computer you're running?

Stuff like the type of processor, or how much RAM.

How are you trying to install it? CD/DVD, USB?

Maybe the disk drive is going bad (It happens, laser eyes can go bad).

The more info we can get, the more we can get to a solution on making the machine hum again.

Can you run a live session off the cd/dvd/usb? (It's usually listed as "try Ubuntu")

If you can, the livecds have gparted on them, and you can format/repartition/fix it with that, hopefully.

Of course, the hard drive might very well be junked, in which case an eventual replacement could bring it back to life.

---

