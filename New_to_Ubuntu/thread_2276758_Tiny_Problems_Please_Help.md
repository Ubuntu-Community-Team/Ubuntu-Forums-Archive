---
title: "Tiny Problems Please Help"
date: 2015-05-04
forum: New to Ubuntu
---

### Post by umut6 on 2015-05-04
Hello everyone,

I have installed (Kubuntu 15.04) 2 days ago and im very happy with it; however, i struggled with some issues that i really can't solve it:

Problem 1: Everything i configure on my desktop reverse back to default after restarting my laptop.For example; wallpaper, folder size, desktop style (i want folder style but it reverses to desktop style).I really need to solve this, otherwise how will i configure my desktop?

Problem 2: I believe this problem is somehow connected to problem 1; after restart some folders come as opened and minimized such as web browser, terminal etc. (i think, programs that i used but did not close before restarting).When i try to maximize them, the folder goes out of screen! i mean, seriously it goes right side of the screen and i can't reach it no matter what.. i think laptop thinks like the screen is at right side.The only solution i found for this is to close the folders and then change from "desktop style" to "folder style" and after that restart the programs.But when i restart the laptop it will happen again.[SOLVED]

Problem 3: When i try to restart/close laptop i see an instantaneous (plasma 5 desktop crash) or its name is something like that but its so fast i can't do any action and laptop restarts as i commanded to.[SOLVED]

Problem 4: A few times laptop stuck at Kubuntu logo, did not go on.So i had to power off and restart it.

Information Notes: 
- I'm a new linux user, this is the first time i'm using a linux os
- I have also a windows 7 on my laptop (for work), but its completely seperated with my Kubuntu [250 GB for windows 7 - 250 GB for Kubuntu]
- I had no problem during installing Kubuntu, just one time frozen but after off/on it was ok.I seperated hard disk as suggested (swap, home and root)
- I'm using a Nouveau display driver which is not bad; but i believe my original driver for GT 520M will give a lot higher performance.I tried to install (.run) file from NV&#304;D&#304;A but it wasn't that easy because of interruptions/fails by X server.Note that NV&#304;D&#304;A binary driver is worse than Nouveau.I haven't tried to play action-high graphic games yet, the real performance will be seen then (really no time for it these days / hard work).By the way, is there an interface in (k)ubuntu like device manager in windows os?

ED&#304;T: 
- I updated the system immediately after the installation, its up to date.
- My system specs:
  Brand: Casper Nirvana A15 (Pegatron) (I don't know its a local brand or an international)
  RAM: 8 GB
  HDD: 500 GB Split in two as 250 GB for windows and 250 GB for Kubuntu.
  Graphic Card: * NV&#304;D&#304;A GForce GT520
                          * &#304;ntel Graphics
  (I think i have 2 graphic cards inside)
  Proccessor: &#304;ntel i5
- Problem 2 and problem 3 are solved.The only thing i did is to "save session" before shut down/restart.However, configuration and freeze at Kubuntu logo problems goes on..

I used Kubuntu forum but couldn't have enough help.If you could help me, i will really be pleasured.I'll check this thread in every 2-3 hours so that i'll see your posts and give you necessary information immediately.

Thank you.

---

### Post by buzzingrobot on 2015-05-04
KDE has a setting in Systems-Settings->Startup&Shutdown that determines if applications that were open when you close down or reboot are restored when you start KDE up again.  If that's set to 'on' by default, turning it off should keep those apps from reopening and, at least, bring a bit of sanity to your problems.

When you install an Nvidia driver from the Nvidia site (the .run file) X needs to be *not* running.  I remember seeing a warning the last time I tried the .run approach (it's been some time).

Kubuntu has a "Driver Manager" tool which will examine your system and present the proprietary drivers it believes are best for your system. Typically, 3-4 are offered, with one being recommended.  These are Nvidia drivers, from Nvidia, tested and packaged by Canonical for Ubuntu. If you can cleanly remove the Nvidia driver you tried to install, I recommend using Driver Manager. (If it's not in the menu, search for it there.)

If you find the Nouveau driver is adequate, consider staying with it. Nvidia develops its drivers independently of the Linux kernel process, provides only a compiled 'blob' and no source code, and problems when one or the other is updated are not unknown (rebooting to a black screen).

The Linux kernel is very good at detecting hardware components, and installing and using the appropriate drivers.  There's little or no need for the kind of 'Driver Manager' Windows uses.

I don't have a clue what's causing the distorted display, sorry.  But, I'll suggest using Nouveau until you get it sorted out, to avoid any Nvidia complications.

Providing the rest of the specs about you hardware -- manufacturer, CPU, RAM, disks, etc. -- will help anyone else that comes along here.
(And did you update the system after the installation?)

---

### Post by SeijiSensei on 2015-05-04
Your personalized KDE configuration is stored in the "hidden" directory $HOME/.kde.  You can insure that any changes you make are preserved by logging out of KDE then logging back in again.  If the machine is shutdown uncleanly like by turning the power off, you are not guaranteed to get any files intact unless you explicitly saved them before turning off the power.  Which applications are open and how they are arranged can also reflect a session from before turning off the power for the same reasons.  Logging out will preserve your entire user environment.

I have had the same experience as you of needing to turn off the machine's power and potentially losing some open files.  I have had persistent issues with power management on my HP dv6t and on an ASUS netbook that preceded it.  If I leave the machine on overnight, there is some chance the entire user interface will be frozen the next morning.  I don't have this problem on an ASUS desktop I own though.  I suspect it has something to do with the power management systems and settings on the laptops.  

The Driver Manager now resides within System Settings which appears in the main menu.  It's at the bottom in the System Administration section.  Use that to install the proprietary NVIDIA driver.

There really isn't an equivalent I know of to Windows's Device Manager.  You can get a very detailed inventory of your system's hardware by running the command "sudo lshw | more".  One reason might be how differently hardware is managed in Linux and Windows.  Microsoft largely off-loads the development and distribution of drivers to the hardware manufacturers so there is more need to know which driver you have and from where.  

Nearly every driver in Linux is open-sourced and included with the operating system kernel as you can see by running:
```

cd /lib/modules/$(uname -r)/kernel
ls

```
You'll see directories containing many different kernel "modules" that contain the code for most basic functions.  The net directory has modules for protocols like IPv4 and wireless.  The drivers directory contains the hardware drivers.  For instance, here's the path on my system with kernel 3.13.0-46-generic to the driver for a bog-standard Intel Gigabit Ethernet adapter:
```
/lib/modules/3.13.0-46-generic/kernel/drivers/net/ethernet/intel/e1000/e1000.ko
```
The "ko" extension stands for "kernel object," I believe.  Unless you explicitly install proprietary drivers like that for your NVIDIA card, all the drivers you're using come standard with the Linux kernel.  They are never managed individually but are updated along with the kernel image as part of standard maintenance.

You can see the list of installed modules with the "lsmod" command.

---

### Post by sandyd on 2015-05-04
> **SeijiSensei said:**
> Your personalized KDE configuration is stored in the "hidden" directory $HOME/.kde.

Its mixed up in ~/.config in 15.04 (Plasma 5). Some socket files remain in ~/.kde

Creates a huge mess to clean up when you want to reset your KDE profile atm.

> **umut6 said:**
> Hello everyone,

I have installed (Kubuntu 15.04) 2 days ago and im very happy with it; however, i struggled with some issues that i really can't solve it:

Problem 1: Everything i configure on my desktop reverse back to default after restarting my laptop.For example; wallpaper, folder size, desktop style (i want folder style but it reverses to desktop style).I really need to solve this, otherwise how will i configure my desktop?

Problem 2: I believe this problem is somehow connected to problem 1; after restart some folders come as opened and minimized such as web browser, terminal etc. (i think, programs that i used but did not close before restarting).When i try to maximize them, the folder goes out of screen! i mean, seriously it goes right side of the screen and i can't reach it no matter what.. i think laptop thinks like the screen is at right side.The only solution i found for this is to close the folders and then change from "desktop style" to "folder style" and after that restart the programs.But when i restart the laptop it will happen again.

> **umut6 said:**
> 
Try
System Settings -> Startup/Shutdown -> Desktop Session -> On Login
Set that to "Start with an empty session"

Problem 3: When i try to restart/close laptop i see an instantaneous (plasma 5 desktop crash) or its name is something like that but its so fast i can't do any action and laptop restarts as i commanded to.

Problem 4: A few times laptop stuck at Kubuntu logo, did not go on.So i had to power off and restart it.

Information Notes: 
- I'm a new linux user, this is the first time i'm using a linux os
- I have also a windows 7 on my laptop (for work), but its completely seperated with my Kubuntu [250 GB for windows 7 - 250 GB for Kubuntu]
- I had no problem during installing Kubuntu, just one time frozen but after off/on it was ok.I seperated hard disk as suggested (swap, home and root)
- I'm using a Nouveau display driver which is not bad; but i believe my original driver for GT 520M will give a lot higher performance.I tried to install (.run) file from NV&#304;D&#304;A but it wasn't that easy because of interruptions/fails by X server.Note that NV&#304;D&#304;A binary driver is worse than Nouveau.I haven't tried to play action-high graphic games yet, the real performance will be seen then (really no time for it these days / hard work).By the way, is there an interface in (k)ubuntu like device manager in windows os?

I used Kubuntu forum but couldn't have enough help.If you could help me, i will really be pleasured.I'll check this thread in every 2-3 hours so that i'll see your posts and give you necessary information immediately.
Thank you.

Don't install using the driver from the nvidia site, it does not work well with Ubuntu.

When Ubuntu has a kernel update, the proprietary graphics drivers (and any other driver that is not included in the Ubuntu kernel by default) need to recompile to work with the new kernel. By default, when using the Driver Manager/Jockey, it installs the drivers from the Ubuntu repos. The drivers there use DKMS to automatically rebuild the drivers when a kernel update is done, thus automatically making the drivers work with the new kernel.

To uninstall the nvidia drivers from the site, just tack --uninstall onto the end of the command used to install it.

For example:
```

sudo NVIDIA-Linux-xxxxxxxx.run --uninstall
```

After a reboot, you can install it from the Driver Manager

---

### Post by umut6 on 2015-05-05
Hello again!

First of all, thank you very much for your helpful approach, you are very kind!

I edited my post, please read ED&#304;T part, i wrote more information for you.

This morning i saved sessions and restarted twice for TEST&#304;NG, both of them i had problem 1 and problem 4.Since it stuck at Kubuntu logo, i had to power off.I strongly believe that as i'm almost very sure, this is a problem about drivers.I had the same problem when i used windows 8 newly released, since drivers were not compatible exactly with my hardwares, this was happening.After i returned to windows 7 at the time, the problem was gone.But i have no clue which driver could cause such a problem and how to solve it in (K)ubuntu?

Edit: Just tested; - Restore previous session (System crash)
                            - Restore manually saved session (System ok)
                            - Start with an empty session (System crash)

it looks like i have to save the session manually not to have system crash.

---

### Post by SeijiSensei on 2015-05-05
Unless you have some strong reason for using 15.04, I'd just install 14.04.  I have 15.04 running in a virtual machine, and I don't see much reason to switch until the transition to KDE5 has some time to settle down.  For most people, using anything other than an LTS release like 14.04 makes little sense unless there is some specific feature of a later version that you need.

---

### Post by buzzingrobot on 2015-05-05
> **SeijiSensei said:**
> Unless you have some strong reason for using 15.04, I'd just install 14.04.  I have 15.04 running in a virtual machine, and I don't see much reason to switch until the transition to KDE5 has some time to settle down.  For most people, using anything other than an LTS release like 14.04 makes little sense unless there is some specific feature of a later version that you need.

Yes, indeed. If you have a system that's working, think twice before moving to any new thing unless you know it delivers something you want and can't get otherwise.

While the new KDE offers users definite and needed improvements in design consistency, the advantages of the new architecture are, at this point, mostly apparent to developers. 

Porting of apps, widgets, etc., to the new environment is ongoing.  Distributions are going to package old and new apps because users expect them to be there. I'd guess it will take a release cycle or so before work on the new environment settles down and KDE distributions sync up with it.

---

### Post by umut6 on 2015-05-05
OK, i'll switch to K14.04 as you recommend, thanks very much for your help ;)

---

