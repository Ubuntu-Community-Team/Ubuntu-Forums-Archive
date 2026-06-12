---
title: "Ubuntu problems [help]"
date: 2020-12-08
forum: New to Ubuntu
---

### Post by 9sito on 2020-12-08
so ive tried ubuntu a few times this year never got it to  run smoothly
 im reaching out for some help 

my set up is is 
```
Aurus x570 elite wifi
Samsung SSD evo 970
Nvidia Geforce GTX 1060
AMD 3700x
G.SKILL Trident Z RGB Series 2X16 (32gb)
```
Problems are
0. ubuntu runs great before i do any updates after update problems start
1. my pc hangs when i try to reboot 
2. when ever i update ubuntu firefox and other programs start freezing or they never want to open (firefox, settings, updater, additional drivers and more)
3. xkill doesnt work either neither does terminal (sudo reboot doesnt seem to do anything)

i have a bunch of issues ive tried ubuntu installing it with wubi and i tried ubuntu installing from iso straight from a usb driver same issue occur 
 honestly ive looked every where and nothing works so im reaching out here


Any suggestions 
 
**right now im dual booting with windows 10 pro**

---

### Post by blackbird34 on 2020-12-08
I see you have a discrete NVIDIA graphics card. What about trying out Pop! OS? It's a variant of Ubuntu which is developed by System76 (a computer supplier that specialises in Ubuntu systems). They have lots of graphical tools to easily manage discrete graphics cards, because they sell monster laptops with dual graphics cards etc. 

See: [https://www.fosslinux.com/39438/switching-graphics-in-pop_os-gui-command-line-ways.htm*](https://www.fosslinux.com/39438/switching-graphics-in-pop_os-gui-command-line-ways.htm*)
You should be able to find an .iso image to try a live USB system here: [https://pop.system76.com/](https://pop.system76.com/)

If you really really want to stick to the same system, you could try running your applications via the terminal and see what it spits out, but I wouldn't know how to help you with that.
Edit: PS: I'm no linux specialist but I think Wubi has been obsolete for several years.

---

### Post by rbmorse on 2020-12-08
Wubi has been depreciated for something like 10 years, so what release of Ubuntu are you trying to install? 

My hardware suite is very similar to yours and Ubuntu performs extraordinarily well. I suspect your issue is associated with the driver for the Nvidia GPU.  I suggest you try the following: 

Download the installation .iso for Ubuntu 20.04 and use your desired Windows tool to prepare a UEFI mode installer flash device.  

Boot the machine from the installer flash device and select "install Ubuntu".  On the third or fourth screen displayed by the installer there will be an option to install third-party and proprietary software and drivers (something to that effect).  Click on the box next to this option to make sure it is enabled.  This will allow the installer to include the proper Nvidia proprietary video driver for your GPU in the installation.  Continue with the rest of the process as prompted.

---

### Post by 9sito on 2020-12-08
can i play games in it can can i dual boot with windows?

---

### Post by CelticWarrior on 2020-12-08
Yes to both but you need to follow the instruction above outlined by rbmorse. And make sure you're booting the installation media in UEFI mode.

I suspect you're either not installing the Nvidia drivers or installing something downloaded from Nvidia which would explain things going south after a (kernel) update.

---

### Post by rbmorse on 2020-12-08
> **9sito said:**
> can i play games in it can can i dual boot with windows?

For the dual-boot setup, select the option to install Ubuntu alongside Windows when the partitioning screen appears.

---

### Post by grahammechanical on 2020-12-08
> neither does terminal (sudo reboot doesnt seem to do anything)

When we use the terminal to shutdown or reboot we need to state a time. For example

```
sudo shutdown -now
```
```
sudo reboot -now
```
```
sudo halt -now
```

This is a quote from the man page for shutdown

```
man shutdown
```

> NAME
       shutdown - Halt, power-off or reboot the machine
SYNOPSIS
       shutdown [OPTIONS...] [TIME] [WALL...]
DESCRIPTION
       shutdown may be used to halt, power-off or reboot the machine.

The first argument may be a time string (which is usually "now"). Optionally, this may be followed by a wall message to be sent to all logged-in users before going down.
The time string may either be in the format "hh:mm" for hour/minutes specifying the time to execute the shutdown at, specified in 24h clock format. Alternatively it May  be in the syntax "+m" referring to the specified number of minutes m from now.  "now" is an alias for "+0", i.e. for triggering an immediate shutdown. If no time argument is     specified, "+1" is implied.

Regards

---

### Post by mastablasta on 2020-12-09
> **9sito said:**
> can i play games in it can can i dual boot with windows? 

you didn't write anything about the operating system. what version is causing you the issues?
also as i know nvidia needs xorg rather than wayland, so you might have to change that at login.

we play old and new games. 
native linux games play natively - for example Half life 2, CS:Go, Dota 2, Team fortress 2...
new windows games work via wine (or the implementations of wine such as Steam Proton, Lutris, Playonlinux or Crossover) 


i have old single core PC with 4GB ram, nvidia GT730. most old windows games run way better on linux that they do on windows XP installed on same PC. 


if you want to just to around with the Ubuntu OS i suggest you install it in virtualbox. it's a lot easier and you can't really mess up your windows 10 install.


finally and most importantly - always make sure you have good backups in place before doing any partition moves, new partition creation and new OS install. basically anything that might overwrite the existing data. once you overwrite the data you will very likely lose it forever.

---

### Post by yancek on 2020-12-09
If you want to dual boot Ubuntu with windows 10, you might try reading the official Ubuntu documentation page at the link below which is quite detailed.  I always prefer to use the manual method (Something Else option) which gives you more control, your choice but I would definitely read the info at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

As stated above, wubi has not been supported for years.  The last release officially supported was 12.04 and the wubi.exe was last included in the 14.04 release.  Wubi as explained on their page, is not expected to work on an EFI machine which is almost certainlys the case with windows 10.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by GrouchyGaijin on 2020-12-13
As a side note, I grew tired of hardware issues with Ubuntu (I imagine hardware issues are a problem for almost all Linux distributions.). I started playing with Linux about 12 to 15 years ago and I am far from an expert, but I do remember in the beginning it was a tremendous chore to get wifi and network printing to work. Hardware issues were a major reason I bought a laptop from ZaReason many years ago. That laptop is still working (or at least it was the last time I booted it over a year ago.), but about a year ago I bought a desktop computer from System 76 - the makers of the above mentioned Pop! OS - to be completely honest I opted for them to install Ubuntu 20.04 of the computer instead of their Pop! OS, the reason being I was already familiar with Ubuntu. What I can say is that I have had zero hardware problems with this machine. The wifi works well and it was actually quicker to set up the HP printer that I have connected into my router on my Linux desktop computer than it was to set up the printer on my son's gaming Windows 10 laptop. So, for what it is worth, my suggestion is to consider buying a system from System 76 when it comes time for you to eventually get a new machine.

I am not an employee of or connected to System 76 in any way other than being  a satisfied customer.

---

### Post by mastablasta on 2020-12-15
we discussed in another thread... many (not all) manufacturers now support linux well and if you bought from them it's the same experience. 

as i found lately it is actually only kernel that is not up to date in ubuntu. i got a laptop for my kid for school and  we had to: 
1. patch kernel with wi-fi driver 
2. add kernel switch due to wrong memory allocation when on battery. 

after adding this it works very well. and i believe both of these would not exist if i loaded newer kernel. well, we will see what happens with next LTS.

In any case, if i bought for example business grade lenovo, or dell with preloaded ubuntu or business grade HP, then the issues are simply not there. the companies provide patches to kernel and hardware works out of the box.

i also assembled a desktop PC. after checking out components online for compatibility, i assembled it and i have to say to this day no hardware issues. i even got the old webcam i took form very old desktop working. and that one never worked before without various commands and work arounds.

---

