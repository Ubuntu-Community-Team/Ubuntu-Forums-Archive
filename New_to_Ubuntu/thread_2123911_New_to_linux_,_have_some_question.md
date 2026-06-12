---
title: "New to linux , have some question"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by Retrias on 2013-03-09
So I downloaded the latest version of ubuntu , just to try it on my old netbook that runs windows xp. Its a lenovo ideapad S10-2
according to the serial on the back 
I installed using unetbootin HDD install or as they cal it over the net "frugal install" since I have no access to USB flashdrive, nor an external cd drive back then, I install it choosing to delete windows.

1. back when I am using USB install , the wifi works fine to download the stuff like language packs , updates and other , but when the install process is finished , suddenly the wifi wouldn't work ? why is that ? according to linlap I have to install a wifi firmware , how would I install this firmware from say a USB flashdrive?

2. The windows xp installation is somehow is still there , can I delete it ? if yes how? I used to try linux on another netbook but as there were too many problem back then , I deleted it by formatting, and it messed my bootloader.

3. I am also going to install linuxmint and dual boot it with ubuntu to try which one I can use as my main OS , what is the easiest way to do this ?

---

### Post by grahammechanical on 2013-03-09
I am assuming that you are using Ubuntu 12.10. Go to System Settings>Software Sources>Additional Drivers tab and see if you are offered a wireless driver. Get one distribution of Linux fully working first. Get one issue solved at a time.

---

### Post by Retrias on 2013-03-09
Do I have to get access to the internet to do this ? Kinda like how windows offer you to download drivers?
Yes I am using 12.10

---

### Post by zrdc28 on 2013-03-09
1. back when I am using USB install , the wifi works fine to download the stuff like language packs , updates and other , but when the install process is finished , suddenly the wifi wouldn't work ? why is that ? according to linlap I have to install a wifi firmware , how would I install this firmware from say a USB flashdrive?

**I would guess that you will have the wifi driver as part of the distro but you did not give us very much info to work with. Do a "lspci"  from terminal and post the results**
That will let us know what type of wireless device you have!

2. The windows xp installation is somehow is still there , can I delete it ? if yes how? I used to try linux on another netbook but as there were too many problem back then , I deleted it by formatting, and it messed my bootloader.

**As far as deleting xp just tell linux to use the whole disk drive and it will take care of that for you!**

---

### Post by Retrias on 2013-03-09
Found out the problem, ubuntu somehow installed on my USB flash drive, how do I format this thing so I can use to install ubuntu on the netbook hdd? and still use it as a flash drive?

PS: Do I need to make a new thread?

---

### Post by bro on 2013-03-09
No need for a new thread. 

How did you install it the first time? Do that again and now make sure to install it on the right disk. 

Don't say you installed it from the same usb that you installed it on because that didn't happen.

---

### Post by fiodev on 2013-03-09
try to install again, i remember when i first tried an install it was intimidating coming from mac and windows. Now I love it don't give up.
pay close attention when you get to the step where you are chosing where to install and choose the option to use the entire disk. make sure the disk is the one that is closest to the size of your hard drive. not the small disk which is your usb. or the existing partition. I actually recommend installing next to windows untill you are confident you can do a proper install without anxiety or the need to ask questions.

---

### Post by Retrias on 2013-03-10
> **bro said:**
> No need for a new thread. 

How did you install it the first time? Do that again and now make sure to install it on the right disk. 

Don't say you installed it from the same usb that you installed it on because that didn't happen.

I installed it with my laptop with an ISO i downloaded from the ubuntu official site , w
by making the USB a live USB using unetbootin
now I have another problem , my usb wouldn't get detected in main laptop at all (the flash drive stays empty), but the rest of my laptop can actually read it

---

