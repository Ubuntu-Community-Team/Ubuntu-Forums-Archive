---
title: "Change Screen Resolution?"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by thetrevorharmon on 2008-11-28
Hello! I'm currently running Ubuntu 8.04. I'm trying to change my screen resolution to 1280×1024 but it only goes up to 1024x768. Every time I try to edit the xorg.conf file it says something about not being able to back up. I currently am using an NVIDIA card. How can i change this?

---

### Post by abn91c on 2008-11-28
did you try sudo dpkg-reconfigure xserver.xorg

---

### Post by doas777 on 2008-11-28
I assume your using nvidia-settings or gedit to set the res, right?
when you change things like res in nvidia-settings, you have to run it as root.

you can do that by hitting alt + f2, and typing 
```

gksu nvidia-settings

OR

gksu gedit /etc/X11/xorg.conf

```

you may also have to set the resolution in System -> Preferences -> Screen Resolution to match your nvidia-settings as well. I had to on one box.

good luck,
franklin

---

### Post by RedRat on 2008-11-28
Try running nvidia-settings in the terminal. When you do this, run the following code;
```
gksudo nvidia-settings
```
You need to run nvidia-settings as root or it will not write your settings to the xorg.conf file. The program, if it is present on your system, should come up and allow you to name both the Monitor and the resolution you want, then it will write it to the configuration file. 

If it comes back says that you it can't find the program, you will have to download and install it. See if it is in Synaptic if you do not have it on your computer.

I use Envyng which installs the correct Nvidia and ATI drivers, and nvidia-settings. See if you have envyng installed, in terminal run:
```
gksudo envyng -g
```

You need to run nvidia-settings as root or it will not write your settings to the xorg.conf file.

---

### Post by thetrevorharmon on 2008-11-28
> **doas777 said:**
> I assume your using nvidia-settings or gedit to set the res, right?
when you change things like res in nvidia-settings, you have to run it as root.

you can do that by hitting alt + f2, and typing 
```

gksu nvidia-settings

OR

gksu gedit /etc/X11/xorg.conf

```

you may also have to set the resolution in System -> Preferences -> Screen Resolution to match your nvidia-settings as well. I had to on one box.

good luck,
franklin

well I edit the xorg.conf and this is what I changed:
```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

but I didn't see any change. When I try the other options, they keep opening up an NVIDIA settings program that only allows up to 1024x768. Any suggestions?

---

### Post by doas777 on 2008-11-29
did you add the driver and busid under the device? 

have you looked at the res available in System -> Preferences -> Screen Resolution ? I had to set them before it would allow me to use my nvidia-settings profile. 

intrepid doesn't use the xorg.conf by default, but it was my understanding that if you had configured it, those settings would override the automatic detection. 

you can check the xorg.0.log (system -> administration -> system log) to see what your system is autodetecting. it may give you a clue as to teh source of the problem.

good luck

---

### Post by thetrevorharmon on 2008-11-29
> **doas777 said:**
> intrepid doesn't use the xorg.conf by default, but it was my understanding that if you had configured it, those settings would override the automatic detection. 

I'm running 8.04...that isn't intrepid right? that's hardy or something like that? Are they different?

---

### Post by wolfen69 on 2008-11-29
try in terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart x or reboot.

---

### Post by geofff on 2008-11-30
If you're not using a "US" keyboard layout when doing sudo dpkg-reconfigure -phigh xserver-xorg **BEWARE**
When I did this it reset my keyboard to "us" when my keyboard is a "gb" layout. When I restarted the machine whatever I did I couldn't input the password. I had to reload the old xorg file in console mode and edit the file. 
I therefore strongly recommend that anyone doing this checks the new xorg file to make sure the keyboard layout is as intended before restarting

Otherwise the instruction is brilliant, Thanks

Geofff

---

### Post by thetrevorharmon on 2008-12-02
I tried this code:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and it gave me this:
```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081201222516

```
...what now? that warning keeps coming up (i did indeed try it more than once)

---

### Post by dwasifar on 2008-12-02
That warning is normal.  It's just telling you that it is rewriting your configuration file (which is the point of the thing) and saving a backup.  The backup is useful in case you made a mistake and the new config file completely hoses your xorg and drops you to text on boot; copying the backup back to /etc/X11/xorg.conf restores your previous settings.

If you don't have the proper driver that supports the desired resolution, or your driver supports it but your card doesn't, you can edit xorg.conf until you're blue in the face and you'll still never get that resolution in your settings.  

As others have already said, I recommend running Envy to make sure you have the best driver installed for your hardware.  Do this:

```
sudo apt-get install envyng
```

If that results in a suggestion to install something else, like envyng-gtk for example, then install that instead.  Then run it, either from the menus or from the command line.  It should tell you what the recommended driver is for your hardware and offer to download and install it.  Do that, then reboot.  If you don't see the resolution you want after that, your hardware probably doesn't support that resolution.

---

### Post by geofff on 2008-12-02
It means it has created a new xorg.conf file with new configuration info in it and renamed the old one xorg.conf.20081201222516. If for any reason the new one causes problems the old one can be reinstated from this. Hopefully though this won't be necessary.

Geofff

---

