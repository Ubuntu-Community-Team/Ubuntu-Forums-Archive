---
title: "[SOLVED] Mic and sound problems"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-08-06
Hy all!
I am using Ubuntu 8.04 and I have a little problem (or problems).
First, my build in microphone doesn't work (I have an Asus F3T laptop).So, when I want to talk to somebody on skype I have to plug an external mic (it works fine in Windows, so it's not a hardware problem).
Second, I have a problem with controlling sound.The sound itself works fine, but the volume control won't let me do anything.I can pull down the volume bar, but when I unclick it, it jumps back to max.
This is how my volume control looks like.
Any help would be appreciated.

---

### Post by plucky on 2008-08-06
In your **Volume Control** window go to **Edit > Preferences** and tick "Master","PCM","Microphone","Mic Boost","Mic Select" will help you control your microphone and sound output.

> Second, I have a problem with controlling sound.The sound itself works fine, but the volume control won't let me do anything.I can pull down the volume bar, but when I unclick it, it jumps back to max.

The PCM control seem to control the volume in mine and is adjustable in the GUI window.

Good Luck

---

### Post by markbuntu on 2008-08-06
You can also try this, right click on the volume control. In the window that opens click 

file/change device 

and try a different device. Mine has 13 choices, only one controls my speakers and a different one controls my headphones.

---

### Post by Troll_the_Great on 2008-08-08
> **plucky said:**
> In your **Volume Control** window go to **Edit > Preferences** and tick "Master","PCM","Microphone","Mic Boost","Mic Select" will help you control your microphone and sound output.



The PCM control seem to control the volume in mine and is adjustable in the GUI window.

Good Luck

I only have the following options:"Line-In" "Microphone" "CD" "In-gain" and "Digital-1".The "Microphone" is set to max, but no luck, I can't be heard on Skype for example. 
I enclosed  a screen shot, maybe it will be more explicit.
Cheers!

---

### Post by Troll_the_Great on 2008-08-08
> **markbuntu said:**
> You can also try this, right click on the volume control. In the window that opens click 

file/change device 

and try a different device. Mine has 13 choices, only one controls my speakers and a different one controls my headphones.

Thanks, I managed to control my sound this way.It remains the microphone problem only.
By the way.I'm using a laptop (how I said before) and I have keys to control things, like the volume.When I press them, I can see the icon (look at the screen shot, it will be more explicit) but nothings happens:the volume won't go up and down, and if I use the key for mute, the same.The sound still plays.Any ideas?
Thanks in advance!

---

### Post by markbuntu on 2008-08-08
Your mutimedia keys will only work on the device you have selected in the Volume Control so if you have your mic selected it will control that instead of your speakers. 

In the VolumeControl/Preferences I think you can select multiple things to be controlled by holding down the shift key when you select them.

---

### Post by Troll_the_Great on 2008-08-09
> **markbuntu said:**
> Your mutimedia keys will only work on the device you have selected in the Volume Control so if you have your mic selected it will control that instead of your speakers. 

In the VolumeControl/Preferences I think you can select multiple things to be controlled by holding down the shift key when you select them.

No matter what I choose, it won't work :(
And what about the microphone problem?

---

### Post by markbuntu on 2008-08-09
Ok, you need to go to your mixer. I have gnome-alsamixer myself. If you have no gui mixer, you can open the alsamixer from a terminal:
just open a terminal and type:

alsamixer

You can tab and arrow key around the various sections and make sure that capture is mot muted and is turned up and the same for the microphone. The mic may be in the usb section of the mixer, you just have to play around with the settings.

---

### Post by Troll_the_Great on 2008-08-09
Still no luck.If I type "alsamixer" I get
```
$ alsamixer
alsamixer: function snd_mixer_load failed: No such file or directory
```
If I try "gnome-alsamixer" I get:
gnome-alsamixer

```
(gnome-alsamixer:9505): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed

(gnome-alsamixer:9505): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault
```

I tried reinstalling but with the same result. :(

---

### Post by Troll_the_Great on 2008-08-10
Anybody?

---

### Post by markbuntu on 2008-08-10
That's weird, alsamixer is in the install package and should be there. Have you tried reinstalling all the alsa stuff?

---

### Post by Troll_the_Great on 2008-08-11
If I try to install it this is what I get:
```
sudo apt-get install alsamixer
[sudo] password for troll: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsamixer
```

Weird, no?

---

### Post by Novus on 2008-08-11
As reluctant I am helping someone that fakes a mac desktop...
alsamixer is in the alsa-utils package.
for solving the multimedia keys problem I'v had similar problems and solved them [_this way_]("http://tinkeringnovus.wordpress.com/2008/08/08/control-idevidual-sound-channels/")

---

### Post by Troll_the_Great on 2008-08-11
> **Novus said:**
> As reluctant I am helping someone that fakes a mac desktop...


:)
Is this a bad thing?That's the beauty of linux, it can be made to look exactly how you want.

---

### Post by Troll_the_Great on 2008-08-11
> **markbuntu said:**
> That's weird, alsamixer is in the install package and should be there. Have you tried reinstalling all the alsa stuff?

Yes, I did, but in vain....:(

---

### Post by Novus on 2008-08-11
> **Troll_the_Great said:**
> :)
Is this a bad thing?That's the beauty of linux, it can be made to look exactly how you want.
No, customization ain't a bad thing.. I just get shivers down my spine when I see a half chewed propriety apple on any screen.. but thats not what this topic is about..

Have you checked that system > Preference > sounds > devices > audio conferencing - sound capture is correct?

If you can't start the alsamixer and
```
aptitude reinstall alsa-base alsa-utils
```don't work (post error if you get one) try another mixer.
```
apt-cache search alsa mixer
```
will give a few suggestions

---

### Post by Troll_the_Great on 2008-08-11
I reinstalled what you said, I still get the same error.
Hare is what I got with the other code:
```
sudo apt-cache search alsa mixer
alsa-utils - ALSA utilities
alsa-tools-gui - GUI based ALSA utilities for specific hardware
alsamixergui - graphical soundcard mixer for ALSA soundcard driver
amsynth - two oscillator software synthesizer
ardour - digital audio workstation (graphical gtk2 interface)
aumix - Simple text-based mixer control program
aumix-gtk - Simple mixer control program with GUI and text interfaces
cam - Cpu's Audio Mixer for Linux
gamix - Graphical sound mixer for ALSA
gnome-alsamixer - ALSA sound mixer for GNOME
gom - Command line and interactive ncurses-based OSS audio mixer
kdetv - TV viewer for KDE
moc - ncurses based console audio player
qamix - Configurable mixer for ALSA
xfce4-mixer-alsa - Xfce4 Mixer ALSA backend
```
Now what?

---

### Post by Troll_the_Great on 2008-08-12
Bump!

---

### Post by Novus on 2008-08-12
ok, just installing another mixer just won't work. post the output of:
```
ls /dev/snd
```

```
asoundconf list
```

```
aplay -l
```

```
uname -a
```

```
dpkg -l | grep alsa
```

---

### Post by Troll_the_Great on 2008-08-12
Here is what you asked for:
```
ls /dev/snd
controlC0  hwC0D1    pcmC0D0p  pcmC0D6c  seq
hwC0D0     pcmC0D0c  pcmC0D1p  pcmC0D6p  time
```

```
asoundconf list
Names of available sound cards:
NVidia
```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC861 Digital [ALC861 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
uname -a
Linux My-precious 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
```

```
dpkg -l | grep alsa
ii  alsa-base                          1.0.16-0ubuntu4        
                 ALSA driver configuration files                               
ii  alsa-utils                         1.0.15-3ubuntu2
                 ALSA utilities
ii  gnome-alsamixer                    0.9.7~cvs.20060916.ds.1-1
                 ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                 0.10.18-3
                 GStreamer plugin for ALSA
ii  libesd-alsa0                       0.2.38-0ubuntu9
                 Enlightened Sound Daemon (ALSA) - Shared lib
ii  libpt-1.10.10-plugins-alsa         1.10.10-1ubuntu6
                 Portable Windows Library Audio Plugin for th
ii  libsdl1.2debian-alsa               1.2.13-1ubuntu1
                 Simple DirectMedia Layer (with X11 and ALSA
```

---

### Post by Novus on 2008-08-12
ok, try to run
```
alsamixer -D hw:0
``` and ```
alsamixer -D hw:1
```one of them should bring up the mixer where u'r internal mic is contold from. u'll have to play around and see if you can get it working there.

if -D hw:n don't work try -c 0 and -c 1

---

### Post by Troll_the_Great on 2008-08-13
> **Novus said:**
> ok, try to run
```
alsamixer -D hw:0
``` and ```
alsamixer -D hw:1
```one of them should bring up the mixer where u'r internal mic is contold from. u'll have to play around and see if you can get it working there.

if -D hw:n don't work try -c 0 and -c 1

Still no luck.This is what I get when I run this commands:
```
alsamixer -D hw:0
alsamixer: function snd_mixer_load failed: No such file or directory
```

```
alsamixer -D hw:1
alsamixer: function snd_ctl_open failed for hw:1: No such file or directory
```

```
alsamixer -c 0
alsamixer: function snd_mixer_load failed: No such file or directory
```

```
alsamixer -c 1
wrong -c argument '1
```

Anymore ideas?

---

### Post by Troll_the_Great on 2008-08-13
And another thing.If I try to open Sound Recorder from Applications-Sound&Video, this is what happens:

---

### Post by Novus on 2008-08-13
ok.. the last 2 things I can think of.
```
sudo /etc/init.d/alsa-utils reset
```
If that dosn't work try this
```
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
```

---

### Post by Troll_the_Great on 2008-08-14
> **Novus said:**
> 
```
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
```

Thank you very much, this worked.It fixed both the microphone problem and the shortcut keys too.I ow you one bro!

---

