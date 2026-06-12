---
title: "Screen Resoution"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by dunnicliff on 2008-05-29
Hi all,
I am new to Ubuntu after using XP for ages and it is running well however I cannot change the screen resolution from 800x600.
I have gone to 
Ubuntu Forums > The Ubuntu Forum Community  > Other Community Discussions  > Tutorials & Tips
Reload this Page HOWTO: change resolution/refresh rate in Xorg

to try and change it in the editor section but this is not working so I guess I am doing something wrong! :P 
Is there a step by step process for us newbies who are new to editing code?

---

### Post by bumanie on 2008-05-29
I would try uninstalling and reinstalling the hardware driver for your video card. I had that problem once after an update, after doing the above, everything has worked fine since. Reboot following the uninstall and also after the re-installation. It may not work for you, but it is a simple thing to try prior to editing config files etc.

---

### Post by ardvark71 on 2008-05-29
> **dunnicliff said:**
> Hi all,
I am new to Ubuntu after using XP for ages and it is running well however I cannot change the screen resolution from 800x600.
I have gone to 
Ubuntu Forums > The Ubuntu Forum Community  > Other Community Discussions  > Tutorials & Tips
Reload this Page HOWTO: change resolution/refresh rate in Xorg

to try and change it in the editor section but this is not working so I guess I am doing something wrong! :P 
Is there a step by step process for us newbies who are new to editing code?

Hi...

What is your graphics chipset and driver? This will play a big role in your resolution size.

Best Regards...

---

### Post by Primefalcon on 2008-05-29
do the folliwng in the terminal

```
sudo displayconfig-gtk
```

after configuring said utility to your card and monitior, go back to the terminal and type

```
sudo gedit /etc/X11/xorg.conf
```

and in the following bit

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
```

replace the virtual bit
```
Virtual	1024	768
```

to match what resolution you chose, that'll change the logins screen to your preference so you wont have the monitor keep blipping every time you login or out

---

### Post by iaculallad on 2008-05-29
Try visiting this [thread]("http://ubuntuforums.org/showthread.php?t=807451") on how to manually fix stucked resolution on your /etc/X11/xorg.conf file.

---

### Post by ingrid_ozikem on 2008-05-29
Hello,

1. First run lspci and find out what video card you have. It'll list a whole bunch of things you have but you should be able to find what the video card is (eg. Intel Graphics controller, NVidia , ATI Radeon  etc.. ). IF you want, you can post the output of lspci here for others to look at.

2. If you followed the other guide to edit your xorg.conf, do post your /etc/X11/xorg.conf file contents here. Post it anyway.. 

3. Some simple things you can try by yourself -- run System-> Preferences -> Screen Resolution  ( or run gnome-display-properties directly). it is a nice GUI that can change your resolution under certain circumstances.

4. I'm not sure if this works for everyone but you could also post the output of xrandr -q here.  If xrandr -q lists several possible resolutions that looks something like this,

>  LVDS connected 1280x800+0+1050 (normal left inverted right x axis y axis) 304mm x 190mm
   1280x800       60.0*+   60.0     50.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  


it means your video card recognizes all these resolutions. The one with the * is the one actually being used. 

   Often there are two problems related to resolution -- the video card / driver combination just doesn't know of other resolutions -- or the better resolution modes are defined but just not used. If the latter is the case, xrandr --output LVDS --mode <mode> should be able to set the resolution. Search for xrandr or use the man pages. (Not the most elegant solution perhaps since xrandr is better for changing resolution dynamically at run time and there are more natural ways like in that HowTo for setting the default resolution.)

---

