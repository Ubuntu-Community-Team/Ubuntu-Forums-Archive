---
title: "Stable Nvidia Drivers + Beryl"
date: 2006-12-18
forum: Outdated Tutorials &amp; Tips
---

### Post by JediPottsy on 2006-12-18
***NOTE THIS GUIDE IS FOR PEOPLE USING THE DEFAULT VANILLA KERNEL - IF YOU HAVE COMPILED YOUR OWN KERNEL THIS WONT WORK***

There isn't a decent simple guide for people to install the latest Nvidia drivers, so here's one.

**1)**
The latest stable Nvidia drivers for your Arch can be obtained here:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Download the drivers to your desktop.

**2)**
I am going to install the 1.0-9631 Drivers for 32bit. If you are using drivers other than 9631, then replace the number in the script with your driver.

```


sudo apt-get install linux-headers-`uname -r` build-essential gcc xserver-xorg-dev pkg-config
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-glx-legacy
sudo /etc/init.d/gdm stop
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup265748
sudo sh NVIDIA-Linux-x86-1.0-9631-pkg1.run -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r` 
sudo nvidia-xconfig --no-composite
sudo nano -w /etc/default/linux-restricted-modules-common

sudo /etc/init.d/gdm restart


```This is the code to install your drivers. Note, you need the following script for 64Bit

```

sudo apt-get install linux-headers-`uname -r` build-essential gcc xserver-xorg-dev pkg-config
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-glx-legacy
sudo /etc/init.d/gdm stop
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup265748
sudo sh NVIDIA-Linux-x86_64-1.0-9631-pkg2.run -n -s --x-prefix=/usr/lib64/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r`sudo nvidia-xconfig --no-composite
sudo nano -w /etc/default/linux-restricted-modules-common

sudo /etc/init.d/gdm restart

```Save the file as Install-Nvidia-(driver number), such as "Install-Nvidia-9631" to your root directory

**3)**
load up the terminal and type

```

sudo chmod a+x Install-Nvidia-9631

```(please read the rest before disabling GDM)

**6)**
Press CTRL-ALT-F1 to go to terminal (you can not do this in GUI)

login using your username and password.

```

sudo ./Install-Nvidia-9631

```The script should run through the tasks, until Nano will load with the restricted modules file.

**7)**
In the restricted modules file, type

```

nv

```within the "". Example:

```

DISABLED_MODULES="nv"

```press CTRL+X followed by Y to save the file
The script will restart the GDM and your new Nvidia drivers will be installed.

**Beryl**

**1)**

```

sudo nano -w /etc/apt/sources.list
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install beryl emerald emerald-themes
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup_working_nvidia
sudo nano -w /etc/X11/xorg.conf

```

save the script as Install-Beryl and chmod it

```

chmod a+x Install-Beryl

```

go to terminal (in gui is fine)

run 

```

sudo ./Install-Beryl

```

Your sources list should popup. Scroll down the the bottom and place this text at the bottom of the file

```
deb http://ubuntu.beryl-project.org/ edgy main
```

save the file,
once this is done, the xorg config file should pop-up.
add the following sections to screen and device

```

 Section "Screen"
     [...your configuration...]
     Option "AddARGBGLXVisuals" "True"
 EndSection

```

```

 Section "Device"
     [...your configuration...]
     Option "TripleBuffer" "true"
 EndSection

```

and uncomment the composite lines by placing a "#" infront of it

```

# Section "Extensions"
#     Option "Composite" "Enable"
# EndSection

```

then type

```

sudo reboot

```

this will reboot ubuntu. Once you get back into gnome, press 
ALT+F2 and type in

```
 Beryl-manager 
```

this will launch Beryl....
Have fun!

---

### Post by frodon on 2006-12-18
> **JediPottsy said:**
> 
There isn't a decent simple guide for people to install the latest Nvidia drivers, so here's one.
There're these guides :
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

And even easier the repositories made by tseliot so you can install them with synaptic :
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

