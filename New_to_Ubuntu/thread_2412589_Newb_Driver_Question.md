---
title: "Newb Driver Question"
date: 2019-02-14
forum: New to Ubuntu
---

### Post by forsetti87 on 2019-02-14
So new to Ubuntu since 2007.
May be a dumb question, but I have Ubuntu installed and I'm trying to get drivers all up to date for my hardware.  Can I run the Driver CD that came with the comp or can it not read .exe files.
When I view the drive it shows my external ASUS blu ray reader/burner, however, my only option is format.
I don't know if I'm looking in the wrong area or need to use a terminal command to open it.

The driver CD doesn't auto play.

I can attempt to download drivers, just at the moment I have to download drivers with my wifes windows 10 comp which is horrible. And then transfer over via a Thumb drive.

Because when I attempted with firefox on ubuntu it gave me a page can't be displayed for attempting to access Nvidia drivers. Although the windows comp could access it. Mind you I only have satellite internet at my house.

---

### Post by TheFu on 2019-02-14
Linux doesn't support Windows drivers.  The OSes are not compatible at that level.

---

### Post by mastablasta on 2019-02-15
normally drivers in linux are part of the kernel (core of the OS). some drivers patch the kernel. but some devices do not have linux drivers at all.

option 1 - your device has linux driver but is not in kernel - you can try to install that manually.
option 2 - drivers for your device are in kernel but device is not recognised properly - you need to do some troubleshooting and try to figure out how the device is recognised. read more here: [https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

option 3 - you device does not have linux drivers. hard problem to crack -  solution is to write them, wait for someone to write them or use another device. or use another OS where device is supported. 


for example some models seem to just work others are causing issues: [https://www.linuxquestions.org/questions/linux-hardware-18/external-blu-ray-burner-drives-linux-compatibility-4175613539/](https://www.linuxquestions.org/questions/linux-hardware-18/external-blu-ray-burner-drives-linux-compatibility-4175613539/)

---

### Post by Holger_Gehrke on 2019-02-15
> **forsetti87 said:**
> 
May be a dumb question, but I have Ubuntu installed and I'm trying to get drivers all up to date for my hardware.  Can I run the Driver CD that came with the comp or can it not read .exe files.

Windows drivers won't work in Linux. Drivers for Linux on CDs included with a device are rare. Some network board and RAID controllers come with them.
> **forsetti87 said:**
> 
When I view the drive it shows my external ASUS blu ray reader/burner, however, my only option is format.

Which shows that it's recognized as a burner otherwise that option would not be shown. 
> **forsetti87 said:**
> 
I don't know if I'm looking in the wrong area or need to use a terminal command to open it.

You need an application to burn optical media. K3B and Brasero are the best known candidates. They aren't part of the default install any more because optical media are generally seen as a dying technology.
> **forsetti87 said:**
> 
The driver CD doesn't auto play.

Autoplay of CDs containing Windows Software wouldn't work. In theory there are autoplay mechanisms on Ubuntu but they are switched off by default and their use is discouraged for security reasons.
> **forsetti87 said:**
> 
I can attempt to download drivers, just at the moment I have to download drivers with my wifes windows 10 comp which is horrible. And then transfer over via a Thumb drive.

Because when I attempted with firefox on ubuntu it gave me a page can't be displayed for attempting to access Nvidia drivers. Although the windows comp could access it. Mind you I only have satellite internet at my house.

Do yourself a favour and don't try to install the driver from the website. You'd have to manually fix up the driver after every kernel update. There's a tool to install "additional drivers" that's part of a default install which should install the nvidia driver in such a way that it survives kernel updates.

Holger

---

### Post by oldrocker99 on 2019-02-15
There are people who download the .run file from the nVidia site. It is **not** the way to do it. **If** you have an nVidia card, do this:```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-410
```

Reboot, and you're all done. and if the nVidia driver is updated, you'll automatically get the update, which will not happen with the nVidia .run file.

---

