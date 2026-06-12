---
title: "Wifi card not detected"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by biggerb1 on 2012-11-06
Ok so the title basically says it all. I used ubuntu before (10.04 i think) But i'm still pretty new to it. Last time I installed it on my PC and everything went smoothly, and i was up and running in no time. 

So i thought I'd install it on my laptop. I downloaded ubuntu 12.04 and installed it on my laptop. But it doesn't seem to be able to detect my wifi card. 

Before you ask. Its a Broadcom 802.11g Network Adapter

Now hold up. Yes I've searched the internet for it. And I've come across atleast a thousand threads with the same problem. In all of them. the only way to fix this was to connect to a wired network and download some packages. 

This isn't an option for me, though, as my laptop has a busted network adapter and only wifi connection works.

So i searched for the package and came across the .deb file for the package. Its called "b43-fwcutter_015-9_i386.deb"

I tried to install this in the Ubuntu software center but it said "Only install software from sources you trust"

So, I'm asking you this. Is there any hope that I will be able to run ubuntu on this laptop with internet access?

Thanks in advance for your help. :)

---

### Post by uclugLee on 2012-11-06
If you boot your laptop off the live cd, will it detect your wireless NIC and connect to your network?  If it will, then install from the live cd and when you get to the install options, check the box to download updates during installation.  I had two older Dell laptops with the same issue and this worked for me.

---

### Post by biggerb1 on 2012-11-06
Thanks for the reply. :D

I did boot off of the live CD (kinda).. I used linux live USB maker to make a live bootable USB drive and installed it off of that. Though I did check download and install updates. It did not do so and the "You are not connected to any network" Error would come often during installation. So I'd say that it wasn't detected during installation either.

---

### Post by NikTh on 2012-11-06
Hi , 
if you are sure that this package "b43-fwcutter_015-9_i386.deb" is the appropriate for you , then open a terminal (CTRL+ALT+T keys combo) and install it with dpkg command. 

Example. 

We assume now that the package is in your /home directory then open the terminal and give this command
```
sudo dpkg -i b43-fwcutter_015-9_i386.deb
``` 

Keep in mind that some packages require dependencies , if the dpkg returns an error about missing dependencies , then you have to download them as well. 

Its a little bit pain in the .... to install packages offline. 

Thanks

---

### Post by biggerb1 on 2012-11-06
Hey, thanks for the reply!

I tried what you said. And it installed! It did not give me any error about missing dependencies, But now it shows this in the terminal. 

```
43-fwcutter version 015

A tool to extract firmware for a Broadcom 43xx device
from a proprietary Broadcom 43xx device driver file.

Usage: b43-fwcutter [OPTION] [proprietary-driver-file]
  --unsupported         Allow working on extractable but unsupported drivers
  -l|--list             List supported driver versions
  -i|--identify         Only identify the driver file (don't extract)
  -w|--target-dir DIR   Extract and write firmware to DIR
  -v|--version          Print b43-fwcutter version
  -h|--help             Print this help

Example: b43-fwcutter -w /lib/firmware wl_apsta.o
         to extract the firmware blobs from wl_apsta.o and store
         the resulting firmware in /lib/firmware
khurram@ubuntu:~$ 

```

I'm not sure what to do. The model/make is the right one. Windows shows it as Broadcom 43xx
But I'm not sure what to do now.

Oh and i should probably mention. This package came with an exe file, "sp33008.exe".
Maybe I have to use that for something...?

Any help is appreciated :D

---

### Post by westie457 on 2012-11-06
Hi Follow all the suggestions in this post. [http://ubuntuforums.org/showpost.php?p=11860231&postcount=8](http://ubuntuforums.org/showpost.php?p=11860231&postcount=8) 
Done correctly it should work.

If it fails post back here for other suggestions.

Thank you.

---

### Post by biggerb1 on 2012-11-06
westie I want to hug you right now!! :D:D:D

---

