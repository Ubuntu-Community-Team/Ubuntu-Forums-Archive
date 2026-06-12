---
title: "How to get a good GUI for managing Software Packages and System Settings."
date: 2016-10-19
forum: New to Ubuntu
---

### Post by swb_mct on 2016-10-19
I just installed **16.04 DESKTOP**.  Is there a way to get a GUI interface for selecting from a full library of apps on ***16.04 DESKTOP ***? . . like there was on my **My Ubuntu/Cinnamon **computer that just died?  
Also can I get a GUI firewall configuration manager on ***16.04 DESKTOP ***like on **Cinnamon** and most other Linux distros?

I need a much better GUI for managing system configuration and software packages.  (in my job, I manage firewalls, and many Windows server types, but I don't have time or brains to learn how to manage Linux from the command line).

I just installed **16.04 Desktop **to use as a basic Apache web server (also need SendMail) but I could switch to another Ubuntu version if that would provide good GUI management.

What do you recommend ?


Thanks

---

### Post by mastablasta on 2016-10-19
> **swb_mct said:**
> I just installed **16.04 DESKTOP**.  Is there a way to get a GUI interface for selecting from a full library of apps on ***16.04 DESKTOP ***? . . like there was on my **My Ubuntu/Cinnamon **computer that just died? 

 

i don't know what you had installed but check out synaptic: [https://apps.ubuntu.com/cat/applications/synaptic/](https://apps.ubuntu.com/cat/applications/synaptic/)


> Also can I get a GUI firewall configuration manager on ***16.04 DESKTOP ***like on **Cinnamon** and most other Linux distros?


install GUFW: [https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

> 
I need a much better GUI for managing system configuration and software packages.  (in my job, I manage firewalls, and many Windows server types, but I don't have time or brains to learn how to manage Linux from the command line).

I just installed **16.04 Desktop **to use as a basic Apache web server (also need SendMail) but I could switch to another Ubuntu version if that would provide good GUI management.

What do you recommend ?


are you running a webserver using desktop version ? :)

i would suggest you look into webgui such as for example ajenti. much lighter CPU and memorry footprint. 

also look into Zentyal server as well as Nethserver and ClearOS (both centOS based).


if you really must have a desktop environment then look the into lighter ones (Lubuntu, Xubuntu) or using only a windows manager (e.g. IceWM, Openbox) or a tiled windows manager (such as for example i3). you can also install a server edition and then only basic DE, not the full distro (e.g. install only XFCE4 not the whole Xubuntu desktop).

you should know that adding a desktop to server (which unlike desktop has certain ports open) increases the attack vectors.

---

### Post by Zero_Bytes on 2016-10-19
You could try App Grid  [http://www.appgrid.org/](http://www.appgrid.org/)  You should have the default Ubuntu softwarecentrum, if not do  ```
sudo apt install ubuntu-software
```  For you firewall without command line, do as mastablasta said, use gufw

---

### Post by swb_mct on 2016-10-19
Thanks for all your help.   I just installed the current version of Linux Mint Cinnamon.  Its exactly what I need as a working network engineer with few Linux skills
It has a package manager and it has system admin tools all in GUI

---

### Post by mastablasta on 2016-10-20
> **swb_mct said:**
> Thanks for all your help.   I just installed the current version of Linux Mint Cinnamon.  Its exactly what I need as a working network engineer with few Linux skills
It has a package manager and it has system admin tools all in GUI

Great! Mint is Ubuntu with a few extra apps preinstalled and a few tweaks and ofcourse it has it's own Cinnamon DE. 

it's good to know you've found something for your needs. Please use thread tool to mark this thread as solved.: [URL="https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"][SIZE=2]https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads
[/SIZE][/URL][SIZE=2][/SIZE]

---

### Post by Geoffrey_Arndt on 2016-10-20
I'm a longtime Ubuntu (& Xubuntu) user, but if you feel you really want a gui to manage the Linux desktop, the best two distros for doing that are:

>   OpenSuse
>   Mageia 

Suse especially offers several gui tools that I wish Ubuntu would adopt also . . . things like port forwarding and other more granular networking methods (via YAST).

---

