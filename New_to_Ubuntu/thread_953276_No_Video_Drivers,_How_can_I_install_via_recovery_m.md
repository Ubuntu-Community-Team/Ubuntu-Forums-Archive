---
title: "No Video Drivers, How can I install via recovery mode?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Slick Tricks on 2008-10-20
Yeah, thats basically it, here is the story

I recently got an extra display for my machine, and wanted to run dual screens on Ubuntu, so I found I had to download and use EnvyNG to get drivers for my nVidia 7300LE graphics card. I installed Envy NG and used it to un-install the drivers I was using so that It could install the ones I needed. After the un-installation, It said I needed to re-boot my machine. So I did. my computer started up, I chose to run Ubuntu (I have dual boot) and the Ubuntu loading screen came up. Then, my computer made the sounds of the login screen, but my display showed that it could not use this format (screen went black pretty much)

What Do I do....

---

### Post by eternalnewbee on 2008-10-20
> **Slick Tricks said:**
> Yeah, thats basically it, here is the story

I recently got an extra display for my machine, and wanted to run dual screens on Ubuntu, so I found I had to download and use EnvyNG to get drivers for my nVidia 7300LE graphics card. I installed Envy NG and used it to un-install the drivers I was using so that It could install the ones I needed. After the un-installation, It said I needed to re-boot my machine. So I did. my computer started up, I chose to run Ubuntu (I have dual boot) and the Ubuntu loading screen came up. Then, my computer made the sounds of the login screen, but my display showed that it could not use this format (screen went black pretty much)

What Do I do....

Boot into Ubuntu in safe mode and install the drivers, and see if it is solved like that.
Trial & Error. That's how we learn. Let us know if it worked.
Good luck.

---

### Post by Slick Tricks on 2008-10-20
I can't even see the log in screen, I hear the noise, but I cannot see anything, otherwise I would login to safe mode.

---

### Post by owenrayg on 2008-10-20
Do you have a recovery option under grub?

---

### Post by Slick Tricks on 2008-10-20
Yeah I do, and I have used the fix X thing, which didn't work

---

### Post by owenrayg on 2008-10-20
Well i'm a complete noob at this stuff  but I have a laptop w/Nvidia geforce 8600m that whenever i enable restricted drivers i get a blank screen on reboot :( I think he means in the recovery mode, using the terminal mode, uninstall the drivers. But I'm even noobier than you so who am I to say :). Good luck!

---

### Post by eternalnewbee on 2008-10-20
> **Slick Tricks said:**
> Yeah I do, and I have used the fix X thing, which didn't work

It might sound stupid, but try to leave the computer shut down for a couple of minutes and see what happens at boot. ( strager things have happened ).
Good luck.

---

### Post by loomsen on 2008-10-20
Anything X-related should be done from a root shell at best.

Anyway, most likely, as you say you hear the sound, you have only one display specified in your xorg? 

cat /etc/X11/xorg.conf

and post its output here.


*edit*

You can do so by:

booting into recovery mode, drop to shell, then do:

apt-get install nvidia-kernel-common nvidia-glx-177 nvidia-xconfig

when everything is downloaded and set up, just run

nvidia-xconfig

to get your xorg configured with default nvidia values, which should be more apropriate than "this X thing", which simply purges your xorg.

Now, to see if everything worked, type

startx

If gnome starts, wait till startup is complete, don't do anything else, just wait, and log out again, then reboot and enjoy.

---

### Post by Slick Tricks on 2008-10-20
output too large to fit on my screen, here is what I could see:

Section " device" 
      Identifier.   " configured video device"
End Section

Same for configured monitor and screen, with default screen, configured monitor, and video device,
Is that good?

And no, didn't work, I prolly mucked it up, I put in the command and it said the newest one was alredy installed, so I tried to run nvidia- xconfig but it told me to try from 3 different options

---

### Post by loomsen on 2008-10-20
Not 2 gd no, reconfiguring is rarely good. So every time you decide to reconfigure your X-Server you write this into it. Nothing at all basically.

I'll post a xorg.conf.
Grab it and replace yours with it.
It's pretty basic but it should work if you installed the drivers right.

```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
	Load		"dbe"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection


```

I think I should mention how you should do this.
Copy everything above to a textfile, name it xorg.conf and place it anywhere where it is easily accessible, you home folder, or directly to /.

Start into single user mode, drop to a root shell, and there do (assuming you placed it in ~/ (your $HOME)
```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
rm /etc/X11/xorg.conf
cp ~/xorg.conf /etc/X11/xorg.conf

```
then reboot, and you should see gnome.

NOTE: linux is case sensitive.

So, Xorg.conf is different from xorg.conf as well as xorg.conF.

---

### Post by Slick Tricks on 2008-10-20
okay, but how can I save this text file to use in my root menu, I am using my vista boot to save this text, and I don't know if I will be able to access it... 

also, is there a way I can just use the root menu to tell ubuntu to use the open-source video drivers(that came with ubuntu?) so that I can at least use a GUI to install the nvidia ones?

---

### Post by loomsen on 2008-10-20
> 
You can do so by:

booting into recovery mode, drop to shell, then do:

apt-get install nvidia-kernel-common nvidia-glx-177 nvidia-xconfig

when everything is downloaded and set up, just run

nvidia-xconfig

to get your xorg configured with default nvidia values, which should be more apropriate than "this X thing", which simply purges your xorg.

Now, to see if everything worked, type

startx


I already told you how to install from command line...

---

