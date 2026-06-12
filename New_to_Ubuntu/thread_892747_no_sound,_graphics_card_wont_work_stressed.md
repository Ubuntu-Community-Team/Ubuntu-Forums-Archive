---
title: "no sound, graphics card wont work *stressed*"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by DeadCell on 2008-08-17
Ok, wanted to move from winblows to a nice looking fast OS and chose ubuntu (didnt know anything else) having a few problems, 3rd install and this one i have gotten furthest with.

I have sound, but such a pathetically small amount i have to put my ear next to the speaker to hear it. I have downloaded ALSA but i cant get it to install, throwing back an error when i got to sudo make install.

```
if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /home/deadcell/alsa-driver-1.0.17/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
find /lib/modules/2.6.24-19-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.24-19-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.24-19-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.24-19-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/home/deadcell/alsa-driver-1.0.17/acore'
mkdir -p /lib/modules/2.6.24-19-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.24-19-generic/kernel/sound/acore
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-rtctimer.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/deadcell/alsa-driver-1.0.17/acore'
make: *** [install-modules] Error 1
```

Also when i first tried to install Nvidia drivers for an 8-series ti seemingly worked but when i re-booted after the boot screen it went black although i could still access ctrl-alt-f2 terminal thing. Since then i havent bothered.

My motherboard:
Abit Fatal1ty FP-IN9 SLi 

Any help would be gratefully accepted atm, im so stressed out from this.
//DC//

---

### Post by Naatan on 2008-08-17
I take it you installed Hardy?

ALSA normally comes with hardy so you don't have to install it manually, try tweaking your settings in System > Preferences > Sound

How did you install your nvidia drivers? The best way is by enabling the hardware drive in System > Administration > Hardware Drivers. There enable "NVIDIA accelerated graphics driver"

---

### Post by Sinkingships7 on 2008-08-17
Double click on the speaker icon in the upper right corner of the screen, near your time. Edit -> Preferences. Make sure Master, PCM, and Front are checked. If you have surround sound speakers, you'll want to be sure Surround and Center are checked as well. Press close and proceed to make sure the volume bars are raised to the maximum.

Does your sound work now?

---

### Post by nicedude on 2008-08-17
Assuming you are using Ubuntu here are 3 commands to look at different places sound is controlled

This will open the alsamixer control panel
sudo alsamixer

Here are 2 other Gnome ( the desktop manager of Ubuntu ) sound settings panels

gnome-sound-properties

gnome-sound-recorder

Those 3 should contain all the settings you need to look at and alsa is installed by default so no need trying to compile it.

As far as a simple graphics solution you can either use the restricted driver manager version or install a program called envy-ng which will try to download and install the best driver for your Nvidia or ATI graphics card.

Here is the command to install it

sudo apt-get install envy-ng

then look under Applications -> System Tools -> Envy-ng to run it.

hope this helps and glad you are ditching Windows and trying to use Linux instead, Welcome to the party :-)

---

### Post by kansasnoob on 2008-08-17
As far as the sound try installing gnome-alsamixer either from synaptic (which I prefer) or:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Applications > Sound & Video, lots of toggles:

[ATTACH]81881[/ATTACH]

[ATTACH]81882[/ATTACH]

So many toggles it takes two screenshots!

As far as the Video it sounds to me like you're trying to get 3D out of a video card that just won't support 3D.

---

### Post by DeadCell on 2008-08-17
haha sudo alsamixer worked a charm, thanks alot. Doing the gnome installs now but happy i can hear things again.

As for my graphics card this PC *was* a gaming PC but I dont game anymore, my card is a fairly new 256mb XFX GeForce 8800GT.


Significantly less stressed now. Thank you.
//DC//

---

### Post by Naatan on 2008-08-17
Did you enable the restricted drivers in System > Administration > hardware drivers?

---

### Post by nicedude on 2008-08-17
No if he is correct and using a 8000 series Nvidia card it will most defiantly support 3D and Compiz etc. It will just need a good driver, since your new I would suggest trying the envy-ng program that I suggested earlier as it is made by one of the Admins here and is for Ubuntu to install Nvidia & ATI drivers and should work just fine. It is "Windows" simple to use as well, just when it asks if you would like it to configure your xorg.conf file make sure to say yes as it should do it just fine and to do it by hand can be tricky so just let it do everything for you :-)

While the restricted driver will probably work with compiz ( to give you 3D effects etc ) it also might not, so just try envy-ng and you will get a better/newer driver than restricted one. Glad to see you got your sound going with alsa mixer command your almost there :-)

Heres a further tip before you run into it, I am assuming you are wanting to have compiz 3D effects? If so then install compiz settings manager with the command below and then look under System -> Preferences -> Advanced Desktop Settings. You will also need to right click on your desktop and click "Change Desktop Background" then once that opens click the "Visual Effects" TAB and select "EXTRA" from the list, if this works then your driver for your graphics card is going to support Compiz & 3D etc. If not then you will need a better driver.


HERE IS THE COMMAND TO INSTALL COMPIZ MANAGER
sudo apt-get install compizconfig-settings-manager

Goodluck with your new 3D Ubuntu :-)

---

### Post by nicedude on 2008-08-17
OOPS I goofed earlier with the envy-ng install commands ( I don't use it I install from Nvidia's drivers by hand )

COMMANDS SHOULD HAVE BEEN LISTED AS THESE
this will install both envyng-common & envyng-gtk with is the GTK GUI frontend for it, sorry for incorrect post earlier.

TO INSTALL ENVY-NG
sudo apt-get install envyng-gtk

THEN TO RUN IT
sudo envyng-gtk

---

### Post by DeadCell on 2008-08-17
Cheers but when i try to get envy-ng i get this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envy-ng

```

EDIT: Just saw above post :P

---

### Post by DeadCell on 2008-08-17
Yup all done, everything went nice and smooth. :D

Thanks alot for you help, and so quick aswell.

//DC//

---

