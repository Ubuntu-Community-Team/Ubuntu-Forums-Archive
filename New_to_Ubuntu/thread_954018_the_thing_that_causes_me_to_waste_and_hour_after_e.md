---
title: "the thing that causes me to waste and hour after every time i shut down my computer"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-10-20
ok ok i lied... more like 20 mins, but every time i hit shud down and then start up again, my resolution goes down to 640 x 480 and the only way to fix it is to uninstall my graphics driver, reinstall it, and then restart my computer....  how do i stop this... if i have spelling mistakes in this post its cuz i can only see about half of firefox right now....

---

### Post by oldos2er on 2008-10-20
What video card, and which drivers are you using?

---

### Post by hyperhopper on 2008-10-20
geforce 5200

and latest accelerated graphics driver....

---

### Post by jemate18 on 2008-10-20
seems like driver problems.....

---

### Post by hyperhopper on 2008-10-20
> **jemate18 said:**
> seems like driver problems.....

worked fine on the computer i took it from.......

---

### Post by Ad-Mac on 2008-10-20
I had problems getting the drivers installed correctly on my 7600gs. seems you have to modify software sources to include mutiverse and universe repositories and then download the appropriate restricted drive for your card, prolly, nvidia-177.*, imediately after go to the hardware manager and activate the restriced driver, then restart. you can also do this from the root terminal using "sudo apt-get install updates"  then "sudo apt-get install nvidia-glx-177* you probably already know this, just putting in my two cents.............Ad

---

### Post by hyperhopper on 2008-10-20
@ ad--

WHU???

i already see universe and multiverse, thats the first thing i did, and then hit get new driver.........

---

### Post by hyperhopper on 2008-10-21
bump....

---

### Post by madsc89 on 2008-10-21
You probably have to change this entry in your /etc/X11/xorg.conf file:

```
 sudo gedit /etc/X11/xorg.conf
```

Find the section "screen".

Mine looked like this:
```

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		EndSubSection
EndSection

```

You have to add the line Mode, with you preferred resolution (e.g. "1280x1024") under the subSection Display. Not sure how many you should add, but my problem was too high resolution, and 1280x1024 is standard in my log on screen, and the highest in System -> preferences -> Screen resolution.

I changed mine into this (the preferred resolutions for your screen): 
```

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes		"1280x1024" "1024x768" "1280x960" "640x480" "800x600"

	EndSubSection
EndSection

```

---

### Post by jerome1232 on 2008-10-21
One time I had this problem, blacklisting certain drivers fixed it for me. Did you install with envy or the driver from Nvidia's website? Or did you use the restricted driver manager? If you used the installer off of nvidia's website/envy than this might help. If you used restricted driver manager it won't.
  
(can't seem to find the thread still looking)

---

### Post by eternalnewbee on 2008-10-21
I had the 5200 card and experienced system freezes. If you can afford a new one, do it. If you can't, try disabling the visual effects, reboot and see what happens.
____________________________________


Ubuntu 8.04 Gnome 2.22.2 2.6.24-19-generic
AMD Athlon(tm) XP 899.219 MHz 256 KB
GeForce 7300 GT

---

### Post by hyperhopper on 2008-10-21
to tell you the truth, i forgot how i got it.... sorry,


but im PRETTY sure i saw a pic of a grphics card right next to all the other notifacation icon and clicked on it and it said i could just hit check then install and id be good, (i keep my comp on for days on end, bmy record is 24 days without shutdown...


@ above me--- my comp doesnt work if I use compiz, im just on zero visual effects....

---

### Post by hyperhopper on 2008-10-21
> **Ad-Mac said:**
> I had problems getting the drivers installed correctly on my 7600gs. seems you have to modify software sources to include mutiverse and universe repositories and then download the appropriate restricted drive for your card, prolly, nvidia-177.*, imediately after go to the hardware manager and activate the restriced driver, then restart. you can also do this from the root terminal using "sudo apt-get install updates"  then "sudo apt-get install nvidia-glx-177* you probably already know this, just putting in my two cents.............Ad

> **madsc89 said:**
> You probably have to change this entry in your /etc/X11/xorg.conf file:

```
 sudo gedit /etc/X11/xorg.conf
```

Find the section "screen".

Mine looked like this:
```

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		EndSubSection
EndSection

```

You have to add the line Mode, with you preferred resolution (e.g. "1280x1024") under the subSection Display. Not sure how many you should add, but my problem was too high resolution, and 1280x1024 is standard in my log on screen, and the highest in System -> preferences -> Screen resolution.

I changed mine into this (the preferred resolutions for your screen): 
```

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes		"1280x1024" "1024x768" "1280x960" "640x480" "800x600"

	EndSubSection
EndSection

```

i got this, so i should add after defaultdepth my preferred resolutions?




Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

---

### Post by madsc89 on 2008-10-22
How did you install your driver? Trough ubuntu's respos, or through envy (or similar), or through a downloaded file (.deb, .tar etc.)?

> **hyperhopper said:**
> i got this, so i should add after defaultdepth my preferred resolutions?




Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

I'm not completely sure, so backup your file first.

Then I would add this between Defaultdepth	24 and EndSection:
```
	SubSection "Display"
		Viewport   0 0
		Modes		"1280x1024" "1024x768" "1280x960" "640x480" "800x600"

	EndSubSection
```

Off course with your resolutions. Start with the preferred standard resolution (hopefully the highest).

It would then look like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
            SubSection "Display"
		     Viewport   0 0
		     Modes		"1280x1024" "1024x768" "1280x960" "640x480" "800x600"
	    EndSubSection
EndSection
```

---

### Post by o.besner on 2008-10-22
Sudo apt-get install nvidia-settings nvidia-xconfig

use xconfig to generate a new xorg.conf

---

### Post by AFarris01 on 2008-10-22
installing the nvidia-settings package would be very helpful for you, but just remember that in order for you to make lasting changes with it, you would have to run it is root, i.e. "sudo nvidia-settings" from terminal after you get it installed.  otherwise it won't let you save the new xorg.conf file that it creates.

---

### Post by hyperhopper on 2008-11-28
WHAT IN THE WORLD?

at ad

it can find nvidia-glx-177* to install or remove

AND EVEN THOUGH I GOT A RED ARROW SAYING UPDATES AVAILABLE- IT SAYS CANT FIND UPDATES!!!!

---

### Post by hyperhopper on 2008-11-28
bump

---

### Post by philinux on 2008-11-28
Have you tried the usual.

```
 sudo apt-get update && sudo apt-get upgrade
```

---

### Post by hyperhopper on 2008-11-28
never did a sudo apt-get upgrade, 


and what does && do?

---

### Post by jerome1232 on 2008-11-28
&& makes it execute the next command only if the first command succeeded.


So that will execute 'sudo apt-get update' if that command exits successfully then it will execute 'sudo apt-get upgrade', if 'sudo apt-get update' failed then 'sudo apt-get upgrade will not be executed.

---

### Post by hyperhopper on 2008-12-09
how can i completley uninstall the current driver???

also, how can i get this Envy thing you're talking about?

---

### Post by Zimmer on 2008-12-09
envyng-gtk  from Synaptic Package MAnager (if you are using the GNOME desktop)

---

### Post by hyperhopper on 2008-12-09
how do i uninstall the current driver?

---

### Post by fenian on 2008-12-09
> **hyperhopper said:**
> how do i uninstall the current driver?

You can uninstall the current driver  with Envy,choose to uninstall all Nvidia drivers.

---

