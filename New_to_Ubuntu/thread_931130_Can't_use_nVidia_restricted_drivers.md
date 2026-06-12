---
title: "Can't use nVidia restricted drivers"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by ArtPulse on 2008-09-26
Hey there! I've got this weird problem...

For some reason my display went back. So I tried to install another packages than the ones I use for nVidia on console (as GDM was all black, my LCD screen said "No Input").

So I installed nvidia-glx-new-envy, and I got image. Couldn't use Compiz, so I got EnvyNG for GTK and installed my nVidia drivers with it.

Restarted. Now I can use Compiz, but watching a video on YouTube is deathly slow (I'd say 3 FPS). Movies on VLC work fine. Also I hear a noise coming from my computer when any screen animation is done (like typing, a GIF, moving cursor over menus, etc...).

I went to Restricted Drivers, it's said not to be enabled neither on use. I click on Enable, installs... uninstalls envy... done! restart: black screen... So again back to envy, and now I have "fair" speed at YouTube, yet: THAT NOISE coming from my computer is killing me... It sounds like the computer is playing with a bag of crackers :S "crish crish crish" >.< it's almost a constant noise, even more if I play videos.

I can't install restricted drivers :S can anyone tell me how to do this, and still have screen? I used to have them...

Ubuntu Hardy Heron, Desktop edition
GDM + Gnome
nVidia GeForce FX 5200 - 128 MB
Screen: Acer AL1916W
Thanks!...

---

### Post by nowshining on 2008-09-27
if u install the driver from the nvidia site it shouldn't show as enabled i don't think..anyway download the nvidia drivers manually and install from there.. at the end when asked say yes to config xorg.conf..

---

### Post by ArtPulse on 2008-09-27
Aighty, let's give it a try, why not? =P though I heard it's not recommendable... but hell, xP can this get any worse? =P

Let's see...

---

### Post by ArtPulse on 2008-09-27
Noise still here T_T i didn't have such noise until I downgraded from Gutsy to Hardy.

I can't wait for a new version of Ubuntu, this one complicated my life in all ways, though came with extra facilities I appreciate...

So the noise is still here... Should I... accept this is the way Hardy works?? xP (I don't get any of this on Windows, so i believe it's not my card... Ye Ye I still dual boot)

---

### Post by fenian on 2008-09-27
> **ArtPulse said:**
> ... Should I... accept this is the way Hardy works?? 

No.

I would try to remove all the Nvidia related driver stuff and reinstall clean.
First remove all the Nvidia related driver stuff Open a terminal and enter...

> sudo apt-get renove envyng-core 
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r` envyng-gtk

Restart X with ctrl+alt+backspace

Open a terminal again and enter...

> sudo dpkg-reconfigure -phigh xserver-xorg

Restart X with ctrl+alt+backspace

Install the restricted driver from Administration>Hardware Drivers

---

### Post by ArtPulse on 2008-09-27
aight... let's do that... I'll later, cuz I gtg... but I will! thanks =)

---

### Post by WWSmith36 on 2008-09-27
> THAT NOISE coming from my computer is killing me... It sounds like the computer is playing with a bag of crackers :S "crish crish crish" >.< it's almost a constant noise, even more if I play videos.

This doesn´t sound good; your video card should not make any noise.  My card made noise one time and I opened my box and found a wire was hitting the fan on my video card.

---

### Post by gjoellee on 2008-09-27
May be an issue with flash. You should get the latest flash version. Download it here: [http://www.kshoster.net/node/39](http://www.kshoster.net/node/39)

---

### Post by ArtPulse on 2008-09-27
I know, it shouldn't make any noise xD But it has since I've installed Hardy. IT DOESNT on Windows nor on Gutsy Live CD, Knoppix or other.

Plus, the noise is only under SOME graphical activities, like each GIF animation's frame change, when moving the cursor over menus... and now, that's even more, on each video (flash, VLC, whichever) frame, when using the Fire animation on compiz, etc... And I'm using Normal desktop effects, not Full.

I have no idea what this could be, as it's obviously depending on the refresh the video card has to peform... Neither I think anyone could ever possibly know what this is (I had, have and surely will have the most awkward problems ever with computers xD).

Anyway, let's reinstall the whole thing... wish me luck!

---

### Post by Xiong Chiamiov on 2008-09-27
> **gjoellee said:**
> May be an issue with flash. You should get the latest flash version. Download it here: [http://www.kshoster.net/node/39](http://www.kshoster.net/node/39)
Downloading binaries from untrusted sources isn't really a good idea...

If you can't get things running from clean install, you may try [the newest drivers from NVIDIA]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329"), if you hadn't before.

---

### Post by ArtPulse on 2008-09-27
Aight, here's the thing. I've done eg fenian told me to. If you may wanna check out how the system responded, here is the log:

```
artpulse@px0:~$ sudo apt-get renove envyng-core 
[sudo] password for artpulse: 
E: Invalid operation renove
artpulse@px0:~$ sudo apt-get remove envyng-core 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  envyng-core envyng-gtk
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 1303kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 239410 files and directories currently installed.)
Removing envyng-gtk ...
Removing envyng-core ...
artpulse@px0:~$ sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-glx-legacy-envy for regex 'nvidia-glx*'
Note, selecting nvidia-glx-dev-envy for regex 'nvidia-glx*'
Note, selecting nvidia-glx-dev for regex 'nvidia-glx*'
Note, selecting nvidia-glx-new for regex 'nvidia-glx*'
Note, selecting nvidia-glx-new-envy for regex 'nvidia-glx*'
Note, selecting nvidia-glx-src for regex 'nvidia-glx*'
Note, selecting nvidia-glx-new-dev-envy for regex 'nvidia-glx*'
Note, selecting nvidia-glx-legacy-dev for regex 'nvidia-glx*'
Note, selecting nvidia-glx-new-dev for regex 'nvidia-glx*'
Note, selecting nvidia-glx-envy for regex 'nvidia-glx*'
Note, selecting nvidia-glx-legacy-dev-envy for regex 'nvidia-glx*'
Note, selecting nvidia-glx-legacy for regex 'nvidia-glx*'
Note, selecting nvidia-glx for regex 'nvidia-glx*'
The following packages will be REMOVED:
  linux-386* linux-restricted-modules-2.6.24-16-generic*
  linux-restricted-modules-2.6.24-18-generic*
  linux-restricted-modules-2.6.24-19-386*
  linux-restricted-modules-2.6.24-19-generic*
  linux-restricted-modules-2.6.24-19-openvz* linux-restricted-modules-386*
  linux-restricted-modules-generic* nvidia-glx-new-dev-envy*
  nvidia-glx-new-envy* nvidia-kernel-common* nvidia-settings*
0 upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
After this operation, 272MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 239302 files and directories currently installed.)
Removing linux-386 ...
Removing linux-restricted-modules-2.6.24-16-generic ...
Purging configuration files for linux-restricted-modules-2.6.24-16-generic ...
Removing linux-restricted-modules-2.6.24-18-generic ...
Purging configuration files for linux-restricted-modules-2.6.24-18-generic ...
Removing linux-restricted-modules-386 ...
Removing linux-restricted-modules-2.6.24-19-386 ...
Purging configuration files for linux-restricted-modules-2.6.24-19-386 ...
Removing linux-restricted-modules-generic ...
Removing linux-restricted-modules-2.6.24-19-generic ...
Purging configuration files for linux-restricted-modules-2.6.24-19-generic ...
Removing linux-restricted-modules-2.6.24-19-openvz ...
Purging configuration files for linux-restricted-modules-2.6.24-19-openvz ...
dpkg - warning: while removing linux-restricted-modules-2.6.24-19-openvz, directory `/lib/linux-restricted-modules' not empty so not removed.
Removing nvidia-glx-new-dev-envy ...
rmdir: failed to remove `/usr/lib/nvidia': Directory not empty
Purging configuration files for nvidia-glx-new-dev-envy ...
Removing nvidia-glx-new-envy ...
Purging configuration files for nvidia-glx-new-envy ...
Removing nvidia-kernel-common ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************


************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

Purging configuration files for nvidia-kernel-common ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

Removing nvidia-settings ...
Purging configuration files for nvidia-settings ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
artpulse@px0:~$ sudo rm /etc/init.d/nvidia-*
rm: cannot remove `/etc/init.d/nvidia-*': No such file or directory
artpulse@px0:~$ sudo update-rc.d nvidia-kernel remove
 Removing any system startup links for /etc/init.d/nvidia-kernel ...
artpulse@px0:~$ sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r` envyng-gtk 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  envyng-core nvidia-kernel-common
Suggested packages:
  avm-fritz-firmware-2.6.24-19 nvidia-new-kernel-source nvidia-settings
The following NEW packages will be installed:
  envyng-core envyng-gtk linux-restricted-modules-2.6.24-19-386 nvidia-glx-new
  nvidia-kernel-common
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 5478B/24.2MB of archives.
After this operation, 66.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ftp.usf.edu hardy/restricted nvidia-kernel-common 20051028+1ubuntu8 [5478B]
Fetched 5478B in 0s (5491B/s)         
Selecting previously deselected package envyng-core.
(Reading database ... 238001 files and directories currently installed.)
Unpacking envyng-core (from .../envyng-core_1.1.1ubuntu17_all.deb) ...
Selecting previously deselected package envyng-gtk.
Unpacking envyng-gtk (from .../envyng-gtk_1.1.1ubuntu1_all.deb) ...
Selecting previously deselected package nvidia-kernel-common.
Unpacking nvidia-kernel-common (from .../nvidia-kernel-common_20051028+1ubuntu8_all.deb) ...
Selecting previously deselected package linux-restricted-modules-2.6.24-19-386.
Unpacking linux-restricted-modules-2.6.24-19-386 (from .../linux-restricted-modules-2.6.24-19-386_2.6.24.13-19.45_i386.deb) ...
Selecting previously deselected package nvidia-glx-new.
Unpacking nvidia-glx-new (from .../nvidia-glx-new_169.12+2.6.24.13-19.45_i386.deb) ...
Setting up envyng-core (1.1.1ubuntu17) ...

Setting up envyng-gtk (1.1.1ubuntu1) ...

Setting up nvidia-kernel-common (20051028+1ubuntu8) ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************


Setting up linux-restricted-modules-2.6.24-19-386 (2.6.24.13-19.45) ...

Setting up nvidia-glx-new (169.12+2.6.24.13-19.45) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
artpulse@px0:~$ 


```


All righty... So then, it was time for me to Restart X. I did, and still had GDM. So went to System > Administration > Hardware Drivers. Installed (it didn't download this time, it just told me installation was complete, and that I should restart the system). So I did.

Restarted... black screen T_T!!! kay, so let's install the nVidia latest official drivers so at least I can see... i do it, restart the system... black screen... aighty...

So I use the command
```
# envyng -t
```

and install nVidia drivers with it. Restart the system, voilá! I have graphics again. This noise still stacking at me, everywhere, by the way...

So obviously, it just didn't do the trick. Now... when I say black screen, I mean the following: The GDM tries to connect to the Xserver 4 times. On the first 3, fails, and returns to the current terminal. In a while tries again, fails and comes back to current terminal... On 4th trial it stays. My LCD screen says "Input not supported", but I see my hard drive working as if GDM would be loading normally.

Is there by any chance the xorg.conf is not being configured properly? These versions of Xserver Xorg do not let me configure anything with dpkg-reconfigure, so I cant set resolution, refresh, neither of those...

Maybe the system is failing to recognize them with some drivers all the sudden? Should I give it a push?

This is my actual **xorg.conf**
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Thu Jul 17 18:39:19 PDT 2008
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Option		"NoLogo"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Modes		"nvidia-auto-select"
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"	"CoreKeyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Displaysize	1440	900
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```



This is my previous **xorg.conf**, not working, before installing with EnvyNG:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

Do you think it may work installing the restricted drivers from System > Administration, then replacing xorg.conf with this file??


aaaaaaahhhh I will just give it a try..... xP!

---

### Post by Xiong Chiamiov on 2008-09-27
If you have a working xorg.conf, you *should* be able to just change the driver line from "nv" or "vesa" to "nvidia".  That will enable the proprietary driver, but not change anything else.

---

### Post by ArtPulse on 2008-09-27
Aight so by doing what I said I would do... heh...

I installed restricted, changed xorg.conf into the one that worked, but no luck. So I install the official nVidia drivers I've downloaded again, to after replace it's xorg.conf with the working one... and it did.

Now it says I have restricted drivers and are currently on use, but the noise is still here, maybe it's just gotten worse no matter which driver i use on... Ubuntu Hardy Heron...

So here's another question (still it won't change the fact there's noise, but...) my screen supports 1440x900@60, yet I'm working on 50 Hz because the only two options are 50 and 51 on "Monitor Resolution Settings", and 51 is wierdly displayed.

Any way to be able to choose the real Hz? The mighty 60 Hz?...

My xorg.conf right now is the one I claimed to work on my previous post.

---

### Post by ArtPulse on 2008-09-27
Ah didn't say a word. Did it with  NVIDIA X Server Settings. 60 Hz was the only option (though now on Screen Resolution Settings it's shown as 84 Hz, lol??)

Still... dunno why the noise =S... but hey! I got the latest, working... dunno what else might it be...

Did anyone not get what I mean when I say "noise"? or is it clear? =P

---

### Post by Xiong Chiamiov on 2008-09-27
> **ArtPulse said:**
> 
Did anyone not get what I mean when I say "noise"? or is it clear? =P

This is a noise of some sort from your speakers, correct, not from the actual hardware?

---

### Post by ArtPulse on 2008-09-28
I never wished to be more wrong. But no. And I know quite about audio, tough not much about computer hardware. I could unplug my speakers if I wanted but no, the noise is coming exactly from the graphics card :S unveliable? it could be for me, if I wouldn't have an annoying proof all the time while on Hardy xP (and that's 95% of computer time).

Well to be honest, I can't tell if it comes EXACTLY from the graphics card, but does from inside the computer, around where the audio, video card and other slots are.

I would say it sounds similar to old about-to-die hard disks (but not the same) when looking on looong data...

But I don't hear it coming from the hard disk... though it has 5 years, it's a 120 GB SATA...

Weird, huh? xP

btw: NVIDIA X Server Settings says:

> Peformance Level: 0
Peformance Mode: Maximum Peformance

is my card trying too hard? or not enough?... what do you have set there?

btw I've tried 1024x768@55 and still have the very same noise, I don't think the card is being over demanded...

---

### Post by ArtPulse on 2008-09-28
May I add.. if I turn Desktop Effects off completely, in Appearance, then the noise is almost-completely gone... course I can't work on this, i got used to compiz facilities xP and I used to be fine with this on Gutsy...

---

### Post by nowshining on 2008-09-28
> **ArtPulse said:**
> May I add.. if I turn Desktop Effects off completely, in Appearance, then the noise is almost-completely gone... course I can't work on this, i got used to compiz facilities xP and I used to be fine with this on Gutsy...

if u can turn off the effects then the noise is more than likely the fan - and or something stuck in the actual hardware of the video unit. Since using Desktop effects increases the noise, it may be that the Chip is getting too hot and a the sensor it making the fan spin faster and faster... or it's normal...again with the graphics chip getting hotter and the fan spining faster and stuff..

---

### Post by ArtPulse on 2008-09-29
yeah but... I know when my cooler is going faster, or making noise (I've fixed it many times =P) but this doesnt sounds like a sound a cooler would do. Is totally high pitch, no vibration and...

let's say it's a high pitch 100 ms long sound (0.1 seconds), that happens on each movie frame refresh, each menu refresh, each GIF refresh, etc... If a cooler would be running like crazy, the sound would be constant (and there should be vibration, I'd expect), instead of 100 ms long... of course, this sound is not long and you might say "so what's the prob?"... thing is it's annoying to have MANY of those sounds in only one second xD Right now I'm typing and it barely does any sound, but if I'm watching TV, even if it was on another desktop, there would be noise on each frame...

It's very selective :S...

Is my problem clear now? I just wanna hear "dude, your problem is out of this world" >.< I know there's no solution, maybe begging Intrepid Ibex to be like Gutsy xD

Btw: Turning Effects off at Appearance is enough for the sound to disappear. Let's say it's just 1% out of the noise I have right now, so it's like nothing (I can't hear it, unless I reaaaaaaally try to, and maybe it's just my head).

---

### Post by ArtPulse on 2008-09-29
Uhm! So my dad was around and told him to hear "the noise". I told him to once, and he said it was the speakers xP so this time I turned the amplifier off. Then, i told him to hear
"can't hear anything"

kay... so I clicked on a menu, told him to pay attention, and I moved the mouse up and down over the menu

"yeah, I hear the mouse"

¬¬... so I said: fine, went to YouTube, played a video, and told him: "look! no hands!" for him to finally say: "uhm, must be a capacitor" xP!!! makes sense. For sure it's not the cooler! lol!

So maybe this is the end for my graphic card =( on Hardy Heron, at least xP... it's a GeForce FX 5200, quite old xP...

---

