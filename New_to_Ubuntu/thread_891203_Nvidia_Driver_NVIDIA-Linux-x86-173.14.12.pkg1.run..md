---
title: "Nvidia Driver: NVIDIA-Linux-x86-173.14.12.pkg1.run."
date: 2008-08-15
forum: New to Ubuntu
---

### Post by SidTheKid on 2008-08-15
Is this (*NVIDIA-Linux-x86-173.14.12.pkg1.run*) the right driver for a GeForce 7600GS GPU-based card? The card is an ASUS En7600GS Silent.

The installation instructions seem to indicate that one must open a terminal session and enter the info there to install the driver. Is that the way Linux works for hardware driver installations?

Am I in the right forum for questions of this nature?

Thanx :)

---

### Post by maddog39 on 2008-08-15
If you want to use the proprietary nvidia drivers please use the System > Administration > Hardware Drivers menu. When the dialog comes up, check the box next to the nvidia driver listed. Allow the program to install the driver and reboot as needed. Ater that you should be all set. If there is a particular reason you want to use the ones from nvidia.com then explain and I (or someone else) will post directions for installing those.

---

### Post by crjackson on 2008-08-15
> **SidTheKid said:**
> Is this (*NVIDIA-Linux-x86-173.14.12.pkg1.run*) the right driver for a GeForce 7600GS GPU-based card? The card is an ASUS En7600GS Silent.

The installation instructions seem to indicate that one must open a terminal session and enter the info there to install the driver. Is that the way Linux works for hardware driver installations?

Am I in the right forum for questions of this nature?

Thanx :)

[SIZE="4"]The Ubuntu way[/SIZE] (using graphical menus):
Go to System>Administration>Hardware Drivers - Then check off the boxt that enables the driver and reboot when done.

[SIZE="4"]The Envy way:[/SIZE]
System>Administration>Synapic Package Manager
Click the search button and type Envy - Mark for installation (Envy Core & Envy GTK both should be marked).
CLick the Apply button and it will install Envy.
Close the package manager and go back to the menu on the taskbar panel as follows:
Applications>System>Envy
Once Envy application is launched, select the nVidia driver automatic install and watch it go.  Follow IT'S instructions when done.

[SIZE="4"]The nVidia download way:[/SIZE]
Download the driver to your desktop
Open up a terminal and type ```
cd Desktop
```
do each of the following in a terminl session, you may want to print this out:

```
sudo /etc/init.d/gdm stop
``` - this kills your graphical interface

then run the installer with:

```
sudo sh nvidia-file-name.run
```

then to restart X graphical window manager:

```
sudo /etc/init.d/gdm start
```

Hope this helps...

---

### Post by SidTheKid on 2008-08-15
Thanx, guys.

CR, I printed out your instructions. Many thanks!

Unfortunately, I had already tried the "Ubuntu" way, using System/Admin/Hardware. This does result in the nVidea driver being recognized as being needed, but unenabled. For whatever reason, I then get an error when Ubuntu tries to download the driver. I get a "Can't resolve 'security.ubuntu.com'". What would cause [I]that[?/I]

---

### Post by tech0007 on 2008-08-15
> **SidTheKid said:**
> Thanx, guys.

CR, I printed out your instructions. Many thanks!

Unfortunately, I had already tried the "Ubuntu" way, using System/Admin/Hardware. This does result in the nVidea driver being recognized as being needed, but unenabled. For whatever reason, I then get an error when Ubuntu tries to download the driver. I get a "Can't resolve 'security.ubuntu.com'". What would cause [I]that[?/I]

It usually means the site is busy or down. If that happens again, use the fastest mirror by changing it in System-> Administration-> Software Sources.

---

### Post by SidTheKid on 2008-08-15
Oh, my, I am making this much too complicated by using two different computers with Ubuntu---the main Ubuntu computer (ONLY Ubuntu) is the one with internet access and has proper video display characteristics. The other one is set up to dual boot Ubuntu and Windows XP and does NOT have either a workable wireless adaptor nor a CAT5 interface connector---thus, NO internet capability. On this computer, Ubuntu's screen resolution is way low and I was trying to correct it. This, of course, answers why I get the error message in Ubuntu when I try to download the driver. Duh!

Hey, I've definitely learned some stuff in this process---thanks to you guys being so helpful---that will be useful in the days ahead. Many thanks for helping me get a step closer to being a proficient in the Linux OS.

---

### Post by Yatta99 on 2008-08-15
> **SidTheKid said:**
> Thanx, guys.

CR, I printed out your instructions. Many thanks!

Unfortunately, I had already tried the "Ubuntu" way, using System/Admin/Hardware. This does result in the nVidea driver being recognized as being needed, but unenabled. For whatever reason, I then get an error when Ubuntu tries to download the driver. I get a "Can't resolve 'security.ubuntu.com'". What would cause [I]that[?/I]

Your package list needs to be updated. Go to System>Administration>Synaptic
and after it starts up click on Reload. After it is done you can close Synaptic and retry to load the Nvidia driver.

Tom

---

### Post by SidTheKid on 2008-08-16
Tom, can't do that w/o an internet connection. The computer in question doesn't have connectivity under Linux. Am looking for a U.S.Robotics usb wireless adaptor driver, but, will probably follow good advice I got from a previous post and install a hardwire PCI board and run a cable. That is working fine on my  All-Ubuntu computer.

---

### Post by SidTheKid on 2008-08-16
Happy Day! I am pleased to tell you guys that I found an old wired network card in my closet, installed and connected it to my router, rebooted to Ubuntu and, like magic, my monitor resolution was automatically set to its native resolution of 1680 x 1050 and the display looks GREAT!!!

I also have full internet connectivity. I'm posting this from that very computer. Ubuntu rules!! :):):)

Thanx for all the help. Don't you guys go far away, I know I'll be back very soon with another conundrum for you to help me solve.

**EDIT:** And, Tom, afterwards, I did update as you suggested. Thanx!

---

### Post by subhramani on 2008-08-22
Hey guys....I badly need help here.
I'm a complete newbie to Linux.

When I go to System>Administration>Hardware Drivers, I see a message that there are no proprietary drivers in use and I cant see anything there for me to be able to enable/disable anything.

I tried the "The nVidia download way" mentioned above, but as soon as I kill the graphical interface, I'm able to do nothing.

When I type in "sudo sh nvidia.run", nothing happens. 
NOTE: I have renamed the driver file to nvidia.run.

The only thing I'm able to do is reboot the computer by hitting Ctrl+Alt+Del and nothing else. 
Please help.

I have a GeForce 9600GT and I have downloaded the right drivers from nVidia.com.

Thanks in advance.

---

### Post by Malta paul on 2008-08-22
subhramani, I would download EnvyNG from:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Then install your driver, it will install and ask you to reboot. after your reboot do _not_ tick the box in System>administration>hardware Drivers.
as this will install a less update driver and remove the one just installed by EnvyNG! You will still have 3D graphics.

hope this works for you:)

---

### Post by subhramani on 2008-08-22
Hi Malta...thanks a million for such a quick reply.
I tried installing EnvyNG and selected the first option which is "Install NVidia Drivers", but I get a message "EnvyNG ERROR: Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy's hardwaredetection failed. You can try the manual installation at your risk."

Please see screenshot. 

[[IMG]http://img246.imageshack.us/img246/6468/screenshotsubhramanisubio7.th.png[/IMG]](http://img246.imageshack.us/my.php?image=screenshotsubhramanisubio7.png)

and PLEASE HELP !!!

---

### Post by Malta paul on 2008-08-22
I would give the GUI for EnvyNG a try, Go to Applications>System tools> where you should find EnvyNG. (by the way are you are using Ubuntu 8.04 ?) if not just use Envy.  Try Uninstalling your driver first, then reinstall again.
Good luck:)

Just for info. the Nvidia driver site is:
[http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html)

Here's a Ubuntu forum link that could help:
[http://ubuntuforums.org/showthread.php?t=878948&highlight=nvidia+9600GT](http://ubuntuforums.org/showthread.php?t=878948&highlight=nvidia+9600GT)

---

### Post by subhramani on 2008-08-22
Hi Malta... Thank you very very much!

Used the GUI of EnvyNG, un-installed the existing driver and re-installed it.
WORKS LIKE A CHARM NOW !!!!

Thanks a million for your help.

---

