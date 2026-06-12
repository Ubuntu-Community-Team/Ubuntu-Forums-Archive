---
title: "few problem i had when trying ubunto"
date: 2019-07-11
forum: New to Ubuntu
---

### Post by hothead2 on 2019-07-11
so its was my very first time lunching it. and as much as i like the design i had some functionality issues that i need help with  -firefoxx has consitantly crushed after a few seconds.  -youtube has crushed Immediately if i unblocked java script (i used Ublock origin)  - some add-dons c installed could not installed on Firefox due to the following error: "Installation has being aborted because add on appears to be corrupt"  some software's just didn't lunched.  and i couldn't find  any USB flash drive i have plugged into my PC.  I used the ubunto 18.04 LTS and i have boot it from a USB drive (didnt installed on my PC)  i will be very grateful for any help you can provide :)     Also a bounus question: according to UBUNTO lunching it from USB is "Trying ubunto" does that mean that any insallment i will do will not take place when i restart UBUNTO? the thing is: i still need windows so i prefer not to install ubunto if i dont have to

---

### Post by mastablasta on 2019-07-12
Live session (but form USB/CD and selecting try Ubuntu) is a snapshot of OS in time that is then loaded into RAM. it is meant to try if things work as they should (drivers, hardware...). i can also be used to do some other tasks that can't be done while system is running and hard disks are mounted. so with that in mind...

> **hothead2 said:**
> 
[LIST]
[*]firefoxx has consitantly crushed after a few seconds.  -youtube has crushed Immediately if i unblocked java script (i used Ublock origin)
[*]some add-dons c installed could not installed on Firefox due to the following error: "Installation has being aborted because add on appears to be corrupt"  some software's just didn't lunched.
[*]and i couldn't find  any USB flash drive i have plugged into my PC.  I used the ubunto 18.04 LTS and i have boot it from a USB drive (didnt installed on my PC)  i will be very grateful for any help you can provide
[/LIST]



[LIST]
[*]sometimes this happens in live session and is resolved with full (bare metal) install. when the OS is installed you can do updates which bring in fixes.
[*]same as above - it's a live session, so not everything will work. installing in live session means installing to RAM (especially if persistence was not made when creating USB)
[*]this is a bit more odd, but to know what the PC sees you can use command ```
lsusb
```. this will list all UBS devices. there should also be a GUI for finding devices, but i don't know what it is in Gnome desktop that Ubuntu uses.
[/LIST]

Since you are in "testing mode" it might be worth trying the derivatives such as Kubuntu, Ubuntu Mate, Xubuntu and Lubuntu. 

one thing you might also do is run memtest (maybe overnight) at least 2 times. the issues you experienced could also indicate failing RAM, but it is hard to say since i only have issue description and not what it actually happened and what led to this.  

> 
    Also a bounus question: according to UBUNTO lunching it from USB is "Trying ubunto" does that mean that any insallment i will do will not take place when i restart UBUNTO? the thing is: i still need windows so i prefer not to install ubunto if i dont have to

"trying Ubuntu" as explained above will load everything into ram. when you restart any programs you installed, any changes you made to the OS are lost. if you have a strong enough PC and if you just want to play arround i would suggest to install the OS in a virtualbox. this will make the OS run safely inside windows. since virtualbox needs it's share of resources a lighter desktop such as the one found in Xubuntu is recomended. but if you can pass GPU resource through to virtualbox, then Ubuntu, Kubuntu will work fine.

this guide seems good. use Ubuntu 18.04 version:
[https://brb.nci.nih.gov/seqtools/installUbuntu.html](https://brb.nci.nih.gov/seqtools/installUbuntu.html)

Erase whole disk **in this case** is virtual disk you create, not the actually hard disk with windows on it.

i have very old PC from 2004 or 2005 so i use Xubuntu in virtualbox, because it is lighter on resources. otherwise i use Kubuntu, which is why i don't know the GUi for devices in Gnome

---

### Post by hothead2 on 2019-07-12
first of all thanks for the help:

secondly:
> and if you just want to play arround i would suggest to install the OS  in a virtualbox. this will make the OS run safely inside windows. since  virtualbox needs it's share of resources a lighter desktop such as the  one found in Xubuntu is recomended. but if you can pass GPU resource  through to virtualbox, then Ubuntu, Kubuntu will work fine.

not excactly, my goal is to use ubanto most of the time but switch back to windows when i need to, and in time to ditch Microsoft completely (if it will be possible for me), so i need to be able to easily switch between ubunto on windows,
is this possible?

thirdly:
Xubuntu  and Kubuntu?
what are those? first time im hearing those names.:-s

---

### Post by oldos2er on 2019-07-13
[https://xubuntu.org/](https://xubuntu.org/)

[https://kubuntu.org/](https://kubuntu.org/)

---

### Post by The Cog on 2019-07-13
> Xubuntu and Kubuntu?
what are those? first time im hearing those names.
They are variants of Ubuntu. They have the same operating system underneath, but have different desktop appearances. They all have their own fans. They all have their own installer disks so you can try them out before installing. It's probably worth your time trying each for an hour or so, so you can get a feel for which you would prefer. It is possible to install more than one desktop and then choose which to use when you log in, but that's not the norm - most people have figured out which one they are most comfortable with.

---

### Post by hothead2 on 2019-07-13
> **The Cog said:**
> They are variants of Ubuntu. They have the same operating system underneath, but have different desktop appearances. They all have their own fans. They all have their own installer disks so you can try them out before installing. It's probably worth your time trying each for an hour or so, so you can get a feel for which you would prefer. It is possible to install more than one desktop and then choose which to use when you log in, but that's not the norm - most people have figured out which one they are most comfortable with.

thanks! i will defeintly look this up.
not metter how you look it at however im gonna need to be able to switch between two operating system at the very list becuse i do need windows?
how do i install ubunto while keeping windows exist?

---

### Post by DuckHook on 2019-07-13
> **hothead2 said:**
> thanks! i will defeintly look this up.
Please see the link in my sig: "The Best 'buntu Flavour"
> not metter how you look it at however im gonna need to be able to switch between two operating system at the very list becuse i do need windows?
how do i install ubunto while keeping windows exist?
A previous poster has already pointed you to using a virtual machine. You may wish to reverse that process and install Windows into a VM that is running a bare metal flavour of one of the 'buntus.

You can also consider dual booting. [Instructions here]("https://help.ubuntu.com/community/UEFI").

***WARNING***

If you wish to try dual booting, it is absolutely critical that you make a backup of your data, have Windows reinstallation media prepared, and are expecting and prepared for disaster. Not that it will necessarily happen, but you must be prepared. Otherwise, you are just begging for trouble and tears.

---

### Post by hothead2 on 2019-07-14
i suppose i can give a shot to the VM thing.

but in case im gonna need to dual bot.
what kind of disaster am i soppose to expect?
are we talking about anything irreparable

---

### Post by DuckHook on 2019-07-14
> **hothead2 said:**
> …im working haviliy with programs like adobe premiere and AE. witch is very resource intensive and from what i understood
windows on a VM dont have the same performance.
This is true. If you absolutely *must* use resource-intensive Windows apps, then Windows on bare metal is needed. This means either Windows as a host with Ubuntu in a VM, or dual boot.
> …are we talking about irreperatble damage to the computer itself?
Not physical damage, no. But it is possible to corrupt both OSes so thoroughly that you will have no choice but to reinstall both of them. And if you are not careful, it is possible to mess your partitioning scheme up so that it is difficult even to reinstall. It is also possible to unintentionally erase all data on your HDD. In my case, my data is far more important than any OS (which I find no difficulty in re-installing).

---

### Post by mastablasta on 2019-07-15
i use the old MBR booting system. it was easier then to create dual boot. it is still possible to do that now, but a bit more complicated. in any case my setup is now dual boot. i created a shortcut on linux desktop that i double click and the PC boots into windows. when i reboot in windows i get back to linux. i boot to windows for some games. but before i do that i would try to install them to wine. many work. but many don't. so i need windows to boot to, i am not sure what i will do when this motheboard dies. because i can't use windows XP with new CPU and motherboards. on the other hand it's been a while since i booted to windows.

anyway with SSD dual boot even to windows 10 should be really fast.

---

### Post by hothead2 on 2019-07-17
> [COLOR=#000000]This is true. If you absolutely [/COLOR]*must use resource-intensive Windows apps, then Windows on bare metal is needed. This means either Windows as a host with Ubuntu in a VM, or dual boot.*

ok.. so any good taturial for dual boting?

> 
[COLOR=#000000]Not physical damage, no. But it is possible to corrupt both OSes so thoroughly that you will have no choice but to reinstall both of them. And if you are not careful, it is possible to mess your partitioning scheme up so that it is difficult even to reinstall. It is also possible to unintentionally erase all data on your HDD. In my case, my data is far more important than any OS (which I find no difficulty in re-installing).[/COLOR]


good thing my data is not on the same drive as my Operating system but still, i will make sure to make backup before starting the process

---

