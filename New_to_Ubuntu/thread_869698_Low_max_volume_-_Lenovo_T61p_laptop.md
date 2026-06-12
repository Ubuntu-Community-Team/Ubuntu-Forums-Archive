---
title: "Low max volume - Lenovo T61p laptop"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by raccoonone on 2008-07-25
I installed Ubuntu 8.04 and the max volume is much lower than it is on Windows. I already tried increasing the Master, PCM, and Speaker volume in gnome-alsamixer. I also tried changing the sound playback from Autodetect to ALSA and changing the mixer to OSS. I looked at several threads on these forums and it seems that other people have been having problems with low max volume with Hardy. Does anyone have other suggestions that I could try? The computer is a Lenovo T61p laptop.

---

### Post by oliviacond on 2008-07-25
change the sound playback from ALSA to OSS

---

### Post by raccoonone on 2008-07-25
I just tried that and no luck. I switched the playback to OSS and rebooted, but the sound is still quiet.

---

### Post by gn2 on 2008-07-25
Something to try:

```
sudo nano /etc/modprobe.d/alsa-base

```
Is the following line in that file:

```
options snd-hda-intel model=lenovo

```
If not add it to the end, save and re-boot.

Might work, might not.

Also worth trying removing all the pulse audio packages.

---

### Post by raccoonone on 2008-07-25
Thanks for the suggestion, actually I found this guide: <http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt> late last night and tried adding "options snd-hda-intel model=thinkpad". Unfortunately that didn't work.

I'll look into removing the pulse audio packages, but I tried that on another computer that was having sound problems and it didn't help. Anyone have other suggestions?

---

### Post by arpanaut on 2008-07-25
I just did this guide on my Compaq laptop last night and it cleaned up alot sound issues for me... 

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Give it a good read and apply the parts that apply to you and your system.
Doing the Flash 10 beta thing really made a big dif. with youtube and other streaming stuff. (be aware of AMD-64 and i386 instructions)

HTH

---

### Post by silkstone on 2008-07-25
If you right-click on the volume control icon (top right) and select Preferences, you can change what the volume control actually adjusts.

I remember on one laptop I had the 'Master' setting didn't work too well, and I chose something else which was OK. Obviously some of the options are clearly inappropriate, but you may like to experiment.

---

### Post by raccoonone on 2008-07-25
> **arpanaut said:**
> I just did this guide on my Compaq laptop last night and it cleaned up alot sound issues for me... 

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Give it a good read and apply the parts that apply to you and your system.
Doing the Flash 10 beta thing really made a big dif. with youtube and other streaming stuff. (be aware of AMD-64 and i386 instructions)

HTH
Thanks, I'll take a look at that.
> **silkstone said:**
> If you right-click on the volume control icon (top right) and select Preferences, you can change what the volume control actually adjusts.

I remember on one laptop I had the 'Master' setting didn't work too well, and I chose something else which was OK. Obviously some of the options are clearly inappropriate, but you may like to experiment.
Ya, I looked through the entire Preferences menu, and enabled everything and then maxed out the volume for all the controls. It's still a lot quieter than Windows though

---

### Post by j0rd on 2009-03-27
Right Click Audio control in the top right.

Click preferences

What ever is selected by default (in select). Click master, press close. Push volume all the way to 100%

Repeat these steps again, but now instead of clicking master, click PCM and boost that to 100%.

Fixed the issue for me, but i've always noticed that windows is still louder.

---

### Post by ThomasNovin on 2009-09-23
I have increased both PCM and Master to 100%. Still can't get any good volume on my Lenovo t61p.

---

### Post by ThomasNovin on 2009-09-23
One workaround for VLC:

Start vlc with 'vlc --qt-volume-complete' and you will be able to increase the volume up to 400% which uses software amplification. Works nicely on my machine, doesn't distort the audio.

---

### Post by knowname on 2009-09-24
Could you try typing into a command window:

```
cat /proc/acpi/ibm/volume
```

when I do this I get 

```
level:		7
mute:		off
commands:	up, down, mute
commands:	level <level> (<level> is 0-15)
```

So it appears I have a volume control that is capable of going from 0-15 set at 7. I've seen this referred to in other threads as a type of hardware volume, and all of my software sliders are up all the way. My laptop will get noticeably louder in Windows than in Ubuntu. I think this is the cause, but I have no idea how to change that level.

Curious if other people get the same output from that cat command? Anyone know how to change that level?

---

### Post by ThomasNovin on 2009-09-24
I have the same level set on my system.

I found some documentation on [http://ibm-acpi.sourceforge.net/README](http://ibm-acpi.sourceforge.net/README)

> Volume control -- /proc/acpi/ibm/volume
---------------------------------------

This feature allows volume control on ThinkPad models which don't have
a hardware volume knob. The available commands are:

	echo up   >/proc/acpi/ibm/volume
	echo down >/proc/acpi/ibm/volume
	echo mute >/proc/acpi/ibm/volume
	echo 'level <level>' >/proc/acpi/ibm/volume

The <level> number range is 0 to 15 although not all of them may be
distinct. The unmute the volume after the mute command, use either the
up or down command (the level command will not unmute the volume).
The current volume level and mute state is shown in the file.


Edit: Was able to test it too, didn't change anything on my system. While having a movie playing I changed between 7 to 15 and then down to 0 without any noticeable difference.

---

