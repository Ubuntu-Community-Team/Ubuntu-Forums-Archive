---
title: "Nvidia problem"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by djen9999 on 2008-11-05
Since updating to Intrepid, I've been having display problems.  At first I was getting a blank screen.  I was able to get a display in recovery, but it was only 800x600 instead of the 1280x1024.  I read that I should add the line DeviceSize with my proper resolution and refresh rate to my xorg.conf.  I now have my 1280x1024 but when I boot, I get the warning that I am operating in low graphics.  Everything looks fine except for some artifacting around some fonts and some blurring at different points.  I also do not have 3D nor 2D acceleration.  When I run gksudo nvidia-settings, I get a message that I'm not using the nvidia x driver but in my hardware driver section it says that I'm using version 96.  I also have the option of using 177 or 173 but it doesn't matter which one I use, the results are the same.

My video card is: C51G [GeForce 6100] (rev a2)

This is my output from gksudo gedit /etc/X11/xorg.conf

Section "Monitor"
	Identifier	"Configured Monitor"
	DeviceSize	"1280X1024@60"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

I'm functioning, but just barely, and I would like to have things running properly.  Any help would be appreciated.

---

### Post by djen9999 on 2008-11-05
BTW under Screen Resolution, my refresh rate is set to 0 and can't be chagned.

---

### Post by tuxxy on 2008-11-05
You could try and reconfigure xorg from the terminal, then install the correct driver again

```
sudo dpkg-reconfigure xserver-xorg
```

[http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/)

---

### Post by djen9999 on 2008-11-05
When I reconfigure, I lose my 1280x1024 resolution in the file and I still get a blank screen no matter what driver I use.  I can always get my screen back by inserting the 1280x1024 in the file, but I'm in low graphics mode. The drivers that I'm offered are 173, 177 (recommended) and 96.  Should I try to get a different driver?

---

### Post by WelterPelter on 2008-11-05
I also have a GeForce 6100 and am experiencing the same difficulties. 

For now, my machine can function -- barely -- using the 96 driver.

---

### Post by cariboo on 2008-11-05
I have the same video adapter and I use the 177 driver, it worked perfectly right from the start. The biggest problem I had, was that he servers were so slow when I set it up, It timed out with no indication of what happened, so I restarted and was stuck in a low resolution screen. I changed to a different server and was up and running with the right resolution in 15 minutes.

Make sure all the dependencies get installed too.

Jim

---

### Post by djen9999 on 2008-11-05
Jim,

Did you use the hardware drivers from System > Administration or did you got to Synaptic?  I used all of the drivers that I was offered under System > Administration > Hardware Drivers.  None worked properly.

---

### Post by bodhi.zazen on 2008-11-05
The install from hardware does not work, install the 177 or 173 drivers with apt-get, synaptic, or add/remove.

then 

```
sudo modprobe nvidia
```

Then re-start X (log off and back in or ctrl-alt-backspace)

Then

```
gksu nvidia-settings
```

---

### Post by djen9999 on 2008-11-05
When I enter gksu nvidia-settings, I get an error that I'm not using the nvidia x driver.

Everything else is the same.

---

### Post by WelterPelter on 2008-11-06
> **bodhi.zazen said:**
> The install from hardware does not work, install the 177 or 173 drivers with apt-get, synaptic, or add/remove.

then 

```
sudo modprobe nvidia
```Then re-start X (log off and back in or ctrl-alt-backspace)

Then

```
gksu nvidia-settings
```

This method isn't working for me yet. I get the same black screen as always with 177 or 173. Can you post your Xorg.conf?

---

### Post by mapes12 on 2008-11-06
Hi guys

Don't know if it will work but some have reported success with this HowTo:

[http://ubuntuforums.org/showpost.php?p=6086662&postcount=8](http://ubuntuforums.org/showpost.php?p=6086662&postcount=8)

Best wishes.

Mark

---

### Post by Pconfig on 2008-11-06
Might try 

sudo nvidia-xconfig

(after backing up your xorg.conf file ofcourse)

---

### Post by djen9999 on 2008-11-06
Mapes12, the link sounds scary, but I'm desperate.  I'll let everyone know how it goes.  I wont be trying it until next week however.

---

### Post by nalkari2001 on 2008-11-07
I have just loaded ubuntu 8.10 64 bit desktop and have an onboard Nvidia 6100 video, after trying a few drivers the only one that worked properly was the Nvidia accelerated graphics driver (version 177) [Recommended]. The only limitation is the resolution is limited to 1024 X 768. Hope this helps.:popcorn:

---

### Post by redbob on 2008-11-07
I posted a suggestion days ago that worked out to some of our fellows, he executed> sudo dpkg-reconfigure -phigh xserver-xorg
My card is equal to yours but I'm with Hardy yet.

---

### Post by Peter09 on 2008-11-07
Not sure if you have dione this yet, but this is the first stop for setting up your driver in Intrepid.


Check the output of the terminal command to confirm the driver that you are using.
```
lshw -C display 
```

If the driver is not there or the display is Unclaimed do:-


Configuring your Video Driver:
1. Check that there is no driver waiting to be enabled in System->Administration->Hardware Drivers
2. Boot into recovery mode and select xfix from the menu, this may resolve it. (Check 1. after doing this as well)

---

### Post by djen9999 on 2008-11-07
This is what I get with lshw -C display 



]*-display               
       description: VGA compatible controller
       product: C51G [GeForce 6100]
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:05.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

Everything looks OK.

I tried sudo dpkg-reconfigure -phigh xserver-xorg  a while back and it did nothing.

---

