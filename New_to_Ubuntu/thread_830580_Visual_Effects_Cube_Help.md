---
title: "Visual Effects Cube Help"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by panzerschmack on 2008-06-16
I am a completely new user of Linux. I recently got Heron (8.04) and ran into a snag while trying to get the Cube to run. I managed to download compiz and emerald with a friends help. But, when i try to change my Visual Effects to Extra or Custom, it gives me an error saying "Desktop effects could not be enabled". My system specs are:

eMachine
AMD Sempron Processor 3300+ 2.0 GHz
S3 UniChrome 3D

I have a bad feeling my graphic card isn't powerful enough, but by friend said it's fine...

So, any suggestions?

---

### Post by Corrupt3d on 2008-06-16
System>Administration>Hardware drivers

Check any option that might be related to your graphics card.
Restart your computer.

Hopefully that works.

---

### Post by panzerschmack on 2008-06-16
It doesn't show any driver when i follow your path. I'm assuming there should be...

---

### Post by Corrupt3d on 2008-06-16
> **panzerschmack said:**
> It doesn't show any driver when i follow your path. I'm assuming there should be...

Did you click the left triangle arrow to show all drivers?

Alright then, try this:

Open up a terminal, 
Applications>Accessories>Terminal

Type in:
[quote=]

wget [http://blogage.de/files/4142/download](http://blogage.de/files/4142/download) -O compiz-check

chmod +x compiz-check

./compiz-check[/quote]

This will check to see if your computer can support compiz.
Print your output.

---

### Post by panzerschmack on 2008-06-16
22:42:32--  [http://blogage.de/files/4142/download](http://blogage.de/files/4142/download)
           => `compiz-check'
Resolving blogage.de... 78.46.34.206
Connecting to blogage.de|78.46.34.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27,484 (27K) [application/force-download]

100%[=============================================================>] 27,484        69.60K/s             

22:42:33 (69.50 KB/s) - `compiz-check' saved [27484/27484]


Nothing happens when i type in "chmod +x compiz-check"

and when i type in "./compiz-check" by desktop restarts before i can read anything. This might be related to random hardlocks I've been experiencing. Or maybe I'm doing everything wrong, sorry.

---

### Post by Victormd on 2008-06-16
Open a terminal and type these commands, and post the output (especially of the first one)
```
lspci | grep VGA
```
```
glxinfo | grep rendering
```
If the output of the second one is:
> direct rendering: Yes
Then your driver should be properly installed, but by your previous post, I'm guessing you'll get something different.

The first command will tell you what graphics card driver you have installed and that will allow you to check (google) if it's the latest one, and if not, we can try to help you install the latest one... if it is and compiz isn't working, chances are you won't be able to run it.

---

### Post by Victormd on 2008-06-16
There is a workaround that you can try but the end result might be a bit "choppy" graphics-wise, but let me know if you want to try it anyway and I can try to help you.

---

### Post by panzerschmack on 2008-06-16
First:
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

Second:
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.
direct rendering: Yes

I would like the to try the workaround, just for kicks, and background knowledge. In either case, I hope to purchase a more adequate graphics card in the future.

---

### Post by Victormd on 2008-06-16
Keep in mind that this is not guaranteed to work... :)
backup your xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then install xcompmgr
```
sudo apt-get install xcompmgr
```
from the terminal or search for it in synaptic.

Then edit your xorg.conf:
```
sudo gedit /etc/X11/xorg.conf
```
and add or replace the following line:
> 
Section "Extensions"
Option "Composite" "Enable"
EndSection

You can add the above section anywhere in your xorg.conf, but I would keep it after the block starting with Section "Screen" so it will look something like this:
> 
...
...
...
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection
[B]Section "Extensions"
     Option "Composite" "Enable"
EndSection
[/B]Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection
...
...
...



Let me know if this works...

---

### Post by panzerschmack on 2008-06-16
Unfortunately, did not work. Or, at least, I am still getting the error when I change my Visual Effects to anything besides "None". I think my problem is in the driver: When i reach the point where i need to enable a driver in the Restricted Drivers Manager, it doesn't show anything, whereas every tutorial I've seen has a driver checked.

---

### Post by Victormd on 2008-06-16
did you restart after trying the above?
It seems as if your graphics card doesn't 3D acceleration under ubuntu and if that's the case, then it'll be pretty hard to get the extra effects.

---

### Post by panzerschmack on 2008-06-16
I did restart, to no avail. What process would you suggest for getting the effects to work? In other words, what video card would you suggest?

---

### Post by panzerschmack on 2008-06-16
Also, when i try any run compiz check, my computer screen turns black and brings me to the login screen... Any ideas?

---

### Post by overdrank on 2008-06-16
> **panzerschmack said:**
> Also, when i try any run compiz check, my computer screen turns black and brings me to the login screen... Any ideas?

HI and in my opinion I believe the VIA Unichrome do not support the 3D
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)

---

### Post by panzerschmack on 2008-06-16
When i go here:
[http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220](http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220)
I don't know which one i need, so i go here:
[http://www.viaarena.com/default.aspx?PageID=5&ArticleID=68&P=5](http://www.viaarena.com/default.aspx?PageID=5&ArticleID=68&P=5)
But that doesnt help. How do i know which chipset i have?

---

