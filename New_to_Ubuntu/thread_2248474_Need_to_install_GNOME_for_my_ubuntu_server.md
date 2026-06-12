---
title: "Need to install GNOME for my ubuntu server"
date: 2014-10-15
forum: New to Ubuntu
---

### Post by gurusamy2 on 2014-10-15
I installed ubuntu 14.04.1 server(ubuntu-14.04.1-server-amd64)  through USB and got **black screen**,don't know how to install gnome (userfriendly).

Kindly guide me to install GNOME for my ubuntu server 14.04.1 and let me know the url for downloading gnome package.

Sometime i got error in my laptop:
****************************
1.when i am start my laptop,i got following error .
error:no such partition
eroor:unknown file system

press any key to continue.

and sometime i got this line also

M for manuall recovery.


Thanks
Saravanan

---

### Post by mastablasta on 2014-10-15
server usually does not have any desktops. you can use a webgui such as Zentyal for example.

if oyu really want a desktop on server it might be better to use something lighter. 

if you really want Gnome then try```
 sudo apt-get install gnome-desktop
```

I would suggest something lighter on resources for server. so an lxde-desktop or xfce4-desktop might be better.

Aside from Zentyal I find Ajenti to be a good candidate.

---

### Post by MartyBuntu on 2014-10-15
Would it not make sense just to start over again with a new install Of Ubuntu Gnome?

---

### Post by grahammechanical on 2014-10-15
> [COLOR=#000000]error:no such partition[/COLOR]
[COLOR=#000000]eroor:unknown file system[/COLOR]

That says to me that the boot loader cannot find the partition the Linux kernel is supposed to be in and it does not recognise the format/file system. I simply have no idea how you can install software when Linux itself has not loaded. I doubt very much if installing a GUI desktop of any kind will solve that problem.

Try re-installing. Make a note of the steps that you take and the decisions that you make. Provide some information about the hardware. All of it will help us in trying to guess what is wrong.

Is this server machine? Does it have a graphic adapter? Without a graphic/video card we cannot run a Graphical User Interface (GUI). The capabilities of the graphic adapter will affect the desktop user interface that should be installed.

It is my guess that "M for manual recovery" is the boot loader's way of inviting you to put in boot parameters because the boot parameters that the boot loader has are incorrect.

Regards.

---

### Post by saravanang86 on 2014-10-16
Hi Graphamechanical,
  I have ubuntu 14.04.1 iso image.
Installed in my laptop (via USB as bootable):
I installed in following way.
1.using unetboot software, choosed Distribution as ubuntu and 14.04_live_64.
2.select boot option as USB
3.install ubuntu,english,keyboard slected properly.
4.I did some partition (500GB)
Manually i edited 
C as logical 70GB
D as logical 150GB
E as logical 150GB
F as logical 125 GB as (Selected as / )
remaing 4.2 GB as SWAP and choosed primary memory.
5.I installed ubuntu successfully then  reboot option came and gave reboot and choose option BIOS and bootable as harddisk (primary).
6. sometime is working and mostof the time got error :no such partion,but sometime i got manual recovery and after i press M then went to normal boot.

correct me where i was wrong.

Thanks
Saravanan

---

