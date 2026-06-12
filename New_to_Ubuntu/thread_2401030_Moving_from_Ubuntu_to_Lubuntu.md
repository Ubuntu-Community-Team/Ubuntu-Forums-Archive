---
title: "Moving from Ubuntu to Lubuntu?"
date: 2018-09-12
forum: New to Ubuntu
---

### Post by case963 on 2018-09-12
Q.1 Ubuntu Linux 18.04 runs great on my two laptops. If I were to  install Lubuntu on my two laptops would my two laptops run much better?  My reasoning is because Lubuntu is made for computers with low  resources, so it would make sense that Lubuntu would run like a beast on  a modern stronger computer. I'm a minimalist and don't really care  about aesthetics, and prefer to have my computers to run as best as  possible. 
  
Q.2 are there any drawbacks to switching to Lubuntu even though Ubuntu 18.04 runs great on my two laptops?

  
Q.3 are there any programs from Ubuntu that cannot be installed on  Lubuntu? I have tested Lubuntu on my low spec netbook and so far my test  has indicated that I can put whatever program from Ubuntu to Lubuntu.  The programs I use are Virtual Box, Synergy Software, Emacs, Firefox,  Anki Flashcard software, and on occasion Libre Office. 

  Thank you for any help in regards to my questions.

---

### Post by yancek on 2018-09-12
Pretty much any software available to Ubuntu will be available to Lubuntu as they use the same repositories.  The primary difference is a different DEsktop environment and the fact that long term support for Ubuntu is 5 years and Lubuntu is usually 3 years.

---

### Post by case963 on 2018-09-12
Okay so I don't have to worry about programs. I was advised by someone to just change my Desktop Environment and that it would be the equivalent of installing Lubuntu? I understand that a big difference between Ubuntu and Lubuntu is the Desktop environment but what I am having trouble understanding is whether changing my Desktop Environment in Ubuntu to Lubuntu would be the equivalent of installing Lubuntu as a fresh install?

---

### Post by oldfred on 2018-09-12
The difference is that you will have the Ubuntu desktop files still installed.  And when logging in, will have the choice of which desktop you want to use.

Sometimes user settings may conflict, so I have always preferred to install to a separate partition. But I only install occassionly to test something and have /home inside / (root) and keep all data in separate /mnt/data partition for access from all installs.

Default applications are a lot difference as Lubuntu also only installs the lighterweight applications. You end up having both. If you have hard drive space will not matter, and that is not really a lot. And you may want some of the Ubuntu appllications anyway. 
I install multiple apps from Kubuntu and end up with many of those dependencies, but do not install full Kubuntu desktop into my Ubuntu.

---

### Post by case963 on 2018-09-12
So it would not be the equivalent to a fresh install. I want my computer to run as best as possible, so I think moving to a Lubuntu is a good move because I prefer performance over aesthetics.

---

### Post by DuckHook on 2018-09-13
> **case963 said:**
> So it would not be the equivalent to a fresh install. I want my computer to run as best as possible, so I think moving to a Lubuntu is a good move because I prefer performance over aesthetics.
Your question is not as simple as it first seems, because the answer depends on how much resources you have:

[LIST]
[*]The difference is noticeable and most important when you have weak HW and limited resources. Lubuntu will behave more quickly and leave you more RAM to run apps.
[*]The difference is not noticeable and unimportant if you have powerful HW and lots of resources. You won't sense any difference between the two.
[*]The biggest resource hog in modern GUI computing are the apps; not the OS. A full-fledged browser like Firefox or Chrome, or a big graphics app like GIMP, or a modern game will eat up so much resources that the OS difference is usually just minor in comparison. People who want to keep their OS overhead as light as possible often forget to match lighter weight apps to their skinny OS.
[*]By the same token, if you *must* run heavy apps on a weak machine, then a skinny OS is unlikely to save enough resources to make that much difference.
[/LIST]

---

### Post by mastablasta on 2018-09-13
> **case963 said:**
> So it would not be the equivalent to a fresh install. I want my computer to run as best as possible, so I think moving to a Lubuntu is a good move because I prefer performance over aesthetics.

then explore IceWM, openbox and i3 ;)

also thinking about loading KDE or GNOME apps into Lubuntu ? then it's like having Ubuntu installed (almost).

---

### Post by Impavidus on 2018-09-13
> **case963 said:**
> My reasoning is because Lubuntu is made for computers with low  resources, so it would make sense that Lubuntu would run like a beast on  a modern stronger computer.
Suppose that on a weak computer the Ubuntu OS needs 80% of your resources. That leaves just 20% of your resources for applications. The Lubuntu OS may need just 20% of your resources, leaving 80% for your applications. 20% or 80% for your applications makes a big difference.

On a powerful computer, the Ubuntu OS may need just 4% of your resources, leaving 96% for your applications. The Lubuntu OS needs 1% and leaves 99% for your applications. The difference between 96% or 99% of your resources for applications isn't noticable. So when you have a powerful computer, you can just pick the system with the best looks &#8211; which is, of course, a matter of opinion.

The second big difference between Ubuntu and Lubuntu is the set of default applications. By default, Lubuntu has lighter applications for the same tasks. As DuckHook writes, these lighter applications are what makes it work better on weak hardware.

---

### Post by poorguy on 2018-09-13
Hey case963,

I use *** old desktops ***and would be *** considered substandard*** when compared with computers of today.

All of these desktop computers are very capable and can run ***Ubuntu 18.04*** perfectly well without complaints.

I don't care for all of the ***eye candy crapola*** and I like the ***plain simple ***and** functional** user interface of ***Lubuntu 18.04***.

I recommend a clean install all ***Lubuntu 18.04*** as in my opinion a clean fresh install is the best choice.

***Lubuntu 18.04 ***runs like a bat out of hell on my old desktops.


```
[COLOR=#000000]thomas@Dell-OptiPlex-360:~$ inxi -Fxz
System: Host: Dell-OptiPlex-360 Kernel: 4.15.0-33-generic x86_64 bits: 64 gcc: 7.3.0
Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 18.04.1 LTS
Machine: Device: desktop System: Dell product: OptiPlex 360 serial: N/A
Mobo: Dell model: 0T656F v: A01 serial: N/A BIOS: Dell v: A01 date: 11/28/2008
CPU: Dual core Intel Core2 4300 (-MCP-) arch: Conroe rev.2 cache: 2048 KB
flags: (lm nx sse sse2 sse3 ssse3) bmips: 7180
clock speeds: max: 1800 MHz 1: 1254 MHz 2: 1209 MHz
Graphics: Card: Intel 82G33/G31 Express Integrated Graphics Controller bus-ID: 00:02.0
Display Server: x11 (X.Org 1.19.6 ) drivers: intel (unloaded: modesetting,fbdev,vesa)
Resolution: 1024x768@60.00hz
OpenGL: renderer: Mesa DRI Intel G33 version: 1.4 Mesa 18.0.5 Direct Render: Yes
Audio: Card Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
Sound: Advanced Linux Sound Architecture v: k4.15.0-33-generic
Network: Card: Broadcom Limited NetLink BCM5784M Gigabit Ethernet PCIe driver: tg3 v: 3.137 bus-ID: 02:00.0
IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives: HDD Total Size: 40.0GB (18.7% used)
ID-1: /dev/sda model: WDC_WD400BD size: 40.0GB
Partition: ID-1: / size: 37G used: 7.0G (21%) fs: ext4 dev: /dev/sda1
RAID: No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors: System Temperatures: cpu: 47.0C mobo: N/A
Fan Speeds (in rpm): cpu: N/A
Info: Processes: 139 Uptime: 2:07 Memory: 824.1/3869.7MB Init: systemd runlevel: 5 Gcc sys: 7.3.0
Client: Shell (bash 4.4.191) inxi: 2.3.56
thomas@Dell-OptiPlex-360:~$ inxi -Fxz
[/COLOR]

```

---

