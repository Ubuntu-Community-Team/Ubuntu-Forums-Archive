---
title: "How do i install a tar.gz file"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Linuxidiot on 2008-10-26
So im trying to install these new driver from nvidia main page , linux version. But when i run the sudo command to install it, it tell me that im running a xserver. I have no idea what this means so i followed the link to help me with this problem. When i did it gave me a tar.gz file to manage the xserver i believe....not sure...soo i followed another link from a previous post on how to install software in ubuntu...the link told to me ask the forums...so here i am. I am running hardy8.04 32bit trying to install the drivers for nvidia geforce 9500GT thanks for any help

---

### Post by SunnyRabbiera on 2008-10-26
you may not need it, Ubuntu has a built in tool for this located under system> administration> hardware detection.
Also try envy, its in the repositories.

---

### Post by Linuxidiot on 2008-10-26
i tried to use envy but it does not recognize my card....nor does hardware detection :(

---

### Post by igknighted on 2008-10-26
A tar.gz file is like a .zip file... it is just a compressed archive.

You are talking about .run, or a .bin file.  To run this, the command to run it is, well, just the filename.  You need to specify that you want the file in the current path (hence ./Nvidia...), or use a shell interpreter (sh Nvidia...).

The problem you are having with the xserver are because to change the graphics driver, you have to disable the graphics.  Hit ctrl+alt+f1 to get to a terminal and log in, then type 'sudo /etc/init.d/gdm stop' to stop the graphical subsystems.  Then you can run the driver (with sudo) and it should install.  You might also need the packages 'build-essential' and 'kernel-headers' from apt/synaptic in order to compile the drivers against your kernel.

EDIT: Before you get too into this... run the command 'lspci' and post the results to ensure your graphics card is recognized by the kernel (if it isn't the driver won't help you anyways)

---

### Post by Linuxidiot on 2008-10-26
hanks for the reply....im wondering when you say kernel headers what exactly do you mean cause there is no specific file under that name in the spm

---

### Post by forger on 2008-10-26
linuxidiot:
can you start Applications > Accessories > Terminal and execute this command:
```
lspci
apt-cache policy envyng-gtk
```

Select the output of the command, right-click > copy, then paste it here in a reply.
(Maybe your graphics card isn't detected at all!)

---

### Post by Linuxidiot on 2008-10-26
when i ran the command you said it came out with....00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0640 (rev a1)
...im running a geforce 9500gt....srry i dont know the language yet

---

### Post by jerome1232 on 2008-10-26
edit: Just noticed you tried envy so I removed that part of my post :)

IF this doesn't work try it nvidia's way, all of this should work.
```
sudo envyng --uninstall-all
sudo apt-get install build-essential
put your nvidia installer on you desktop and rename it to nvidia-driver.run
# now press ctrl+alt+F1
sudo /etc/init.d/gdm stop
chmod +x Desktop/nvidia-driver.run
sudo Desktop/nvidia-driver.run
sudo nvidia-xconfig
sudo /etc/init.d/gdm start
```

---

### Post by igknighted on 2008-10-26
> **Linuxidiot said:**
> 01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0640 (rev a1)

This is your graphics card.  Ubuntu isn't recognizing it as the specific model, which is why envy and hardware drivers don't work.  I think if you install the nvidia-glx-new package from synaptic, then run the command 'sudo nvidia-xconfig' in a terminal and reboot, it should work.

---

### Post by forger on 2008-10-26
as recommended above, use **sudo envyng -t** (text version), then choose the newest version available.
(Usually number 0 or 1)

---

### Post by forger on 2008-10-26
Supported by 177.80 driver :)
[http://us.download.nvidia.com/XFree86/Linux-x86/177.80/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/177.80/README/appendix-a.html)
> GeForce 9500 GT 	0x0640

I don't think nvidia-glx-new installation will work, 169.x version didn't support 9500 cards

---

### Post by igknighted on 2008-10-26
I would avoid envy.  It's an old tool for an era when there weren't better tools available.  It's like using a sledgehammer to hammer in a framing nail.  The way I recommended wont cause you any issues when the system updates, whereas envy could leave your system without graphics on an update.

EDIT: That driver didn't get backported into Hardy?

EDIT #2: @OP: You might want to try Intrepid Ibex... it's in RC state now, if you install that and don't have issues, by now the packages should be stabilized for release (as it is later this week) so I bet if you install all updates you will essentially be running 8.10 Final

---

### Post by forger on 2008-10-26
linuxidiot, I think you will have more success if you install it with ubuntu 8.10 intrepid ibex:
[http://releases.ubuntu.com/intrepid](http://releases.ubuntu.com/intrepid)

---

### Post by Linuxidiot on 2008-10-26
so i had tried the command line said by jerome but when i got to the Chmod part it said no directory found...then i had tried the other sugjestion by ignighted and when i tried the sudo nvidia-xconfig command i got the reply of Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'...im going to try and restart now to see if i can get it :)

---

### Post by forger on 2008-10-26
> **igknighted said:**
> I would avoid envy.  It's an old tool for an era when there weren't better tools available.  It's like using a sledgehammer to hammer in a framing nail.  The way I recommended wont cause you any issues when the system updates, whereas envy could leave your system without graphics on an update.

We're talking about **envyng**, they use packages:
[http://packages.ubuntu.com/hardy-updates/nvidia-glx-new-envy](http://packages.ubuntu.com/hardy-updates/nvidia-glx-new-envy) (173.14.12)
Comparing to normal hardy package:
[http://packages.ubuntu.com/hardy-updates/nvidia-glx-new](http://packages.ubuntu.com/hardy-updates/nvidia-glx-new) (169.12)

Updated information:
**neither support** 9500 gt:
[http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/README/appendix-a.html)
[http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.12/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.12/README/appendix-a.html)

Only solution I can think of with the above information, is to install intrepid, it has nvidia driver 177.80-0ubuntu2 currently :)

---

### Post by Linuxidiot on 2008-10-26
well thank you all...i am currently downloading the OS from the link you provided. Srry about the newbness jerome...im sure i just didnt put in the correct path or something...i will post an update about this whole thing in about 1 hour to let you know if this solved my problem :) thanks again

---

### Post by forger on 2008-10-26
When you download it, install it and reboot, log in your account and head to:
System > Administration > Update manager
do all the necessary updates and reboot!

after the reboot, log in your account again and then go to:
System > Administration > Hardware Drivers

Choose to activate/install nvidia accelerated graphics driver (**version 177**)

After that you should only require a reboot! :)

---

