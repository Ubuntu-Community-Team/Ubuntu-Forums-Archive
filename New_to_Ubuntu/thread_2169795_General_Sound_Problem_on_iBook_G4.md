---
title: "General Sound Problem on iBook G4"
date: 2013-08-23
forum: New to Ubuntu
---

### Post by Don_Fuzzel on 2013-08-23
Hey all,

this is my first post here and I hope that this is the right section to ask.

I installed Ubuntu 12.04 for PowerPC on a iBook G4 probably made in 2005. I was having a couple of complications during the installation which I was able to fix by browsing the awesome Ubuntu community.
But now I am trying to get the sound working and even by browsing the community I can't figure out a solution.

It seems to me that no sounds at all are played, I checked out .mp3-Files as well as DVDs. The only sound I ever heard is a chime that comes directly after pressing the start button. This is exactly the same sound it used to play when Mac OS X was still installed.
I already made sure that the volume for the playback software is turned up and I also tried the files as well as the DVDs on a different device.

I tried a couple of troubleshooting steps from the SoundTroubleshooting guide *( [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)* ), but none seems to work. I especially want to point out these Terminal outputs:

Entering [FONT=courier new]sudo aplay -l[/FONT] returns:
[FONT=courier new]aplay: device_list:252: no soundcards found...[/FONT]

Entering [FONT=courier new]lspci -v | grep -A7 -i "audio"[/FONT] doesn't return anything at all.

I am not very experienced with Ubuntu and the terminal and don't fully understand these outputs. Does this mean that the sound card isn't even physically recognized? How do I fix this?

The sound was still working two weeks ago when Mac OS X was installed on it, so I am certain that the sound card should still be working.

Thank you very much in advance. Help would be appreciated.

Don Fuzzel

---

### Post by Don_Fuzzel on 2013-08-24
Alright, after spending another day of research on the issue, I finally found a couple of sources that partially contradicted each other but in the end helped me solve the problem.
As I have the impression that this problem appears from time to time, I hereby share the steps I followed to solve the problem (note that I only tested this on exactly the iBook that I described in Post #1):


[LIST=1]
[*]Make sure that the sound modules are installed by entering this in the terminal:
[FONT=courier new]find /lib/modules/`uname -r` | grep snd[/FONT]A long list of items is supposed to show up. If not, install the sound modules by entering:
[FONT=courier new]sudo apt-get install linux-restricted-modules-`uname -r` linux-generic[/FONT] 
[*]Then open the /etc/modules file:[FONT=courier new]
sudo nano /etc/modules[/FONT]
Make sure that no references to sound modules are written in this file. Particularly delete the lines [FONT=courier new]snd-powermac[/FONT] and/or [FONT=courier new]snd-aoa...[/FONT] if you see them. Then save the file with Ctrl+O and exit with Ctrl+X. 
[*]Then delete the following blacklist by typing:
[FONT=courier new]sudo rm /etc/modprobe.d/blacklist.local.conf[/FONT] 
[*]After rebooting the system [FONT=courier new]aplay -l[FONT=trebuchet ms] [FONT=verdana]will give you this output:[/FONT]
[/FONT][/FONT][FONT=courier new]**** List of PLAYBACK Hardware Devices ****
card 0: SoundByLayout [SoundByLayout], device 0: Master []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/FONT]You made the first big step to the solution as the sound card is now recognized.
[FONT=courier new]lspci -v | grep -A7 -i "audio"[FONT=verdana] still doesn't return anything anyway, because the sound card is not connected via PCI but it is onboard.[/FONT][/FONT] 
[*]Then you type [FONT=courier new]alsamixer[/FONT] and make sure that the master volume is at 100% by using the arrow keys. 
[*]Now use [FONT=courier new]amixer[/FONT] to get a whole lot of information about your sound configuration. I noticed that the value at [FONT=courier new]Simple mixer control 'PCM'[/FONT] is zero. Set it to a moderate value with:
[FONT=courier new]amixer sset 'PCM' 100[/FONT]
The highest possible value is 177 but that will give you a very distorted and overloud sound. I figured that 100 is comfortable. 
[*]This should be it, at least it worked for me. You can check your sound by entering:[FONT=courier new]
aplay /usr/share/sounds/alsa/Front_Center.wav[/FONT]
You should hear a cold, heartless female computer voice claiming that "Front Center", ...whatever. 
[/LIST]

I hope that this will help some people. As you can tell, I am pretty newbie, I hope I didn't describe it too detailed.

**I also just noticed that steps 5 and 6 are reset after every restart. I will try to find a solution to make these changes permanent. If anyone knows the solution for that, please post it.**

These are some of the sources that helped me fix it, but as I said, they partially contradict each other and it was a lot of trial and error for me:
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/201569](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/201569) 
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) 
[http://www.mintppc.org/forums/viewtopic.php?f=15&t=1054](http://www.mintppc.org/forums/viewtopic.php?f=15&t=1054) 
[https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F](https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F)
[http://ubuntuforums.org/showthread.php?t=2020131&page=2](http://ubuntuforums.org/showthread.php?t=2020131&page=2)
[http://wiki.ubuntuusers.de/amixer](http://wiki.ubuntuusers.de/amixer)

---

### Post by Don_Fuzzel on 2013-09-09
Okay, I found out why the settings made with the alsamixer in steps 5 and 6 of my previous post are reset after every restart: 

The reason is that pulseaudio is automatically overwriting all settings made with alsamixer after every restart or booting. To restore the settings automatically, I did this:
[LIST=1]
[*]Make sure the alsamixer-settings are the way you want them. For me, this means:
[FONT=courier new]amixer sset 'Master' 177[/FONT] and then [FONT=courier new]amixer sset 'PCM' 100[/FONT] 
[*]Then you have to save these settings:
[FONT=courier new]sudo alsactl store 0[/FONT] 
[*]Now you need to write a script that restores the settings after pulseaudio has overwritten them:
[FONT=courier new]gedit soundsettingsdelay.sh[/FONT]
Enter these lines:
```

[FONT=courier new]#!/bin/bash[/FONT][FONT=courier new][/FONT][FONT=courier new]

restore_alsa() {
 while [ -z "$(pidof pulseaudio)" ]; do
  sleep 0.5
 done
 alsactl -f /var/lib/alsa/asound.state restore 
}
restore_alsa &[/FONT]
``` 
[*]Save the script and make it executable: [FONT=courier new]chmod +x soundsettingsdelay.sh[/FONT] 
[*]Now add this script to the *Startup Applications*... You can find them in the dropdown menu of the shutdown button. 
[*]This should be it. Restart the system and check if it works without manually restoring the settings. 
[/LIST]

I would never have found that solution without this source, so thanks a lot to its author:
[https://wiki.archlinux.org/index.php/PulseAudio#Pulse_overwrites_ALSA_settings](https://wiki.archlinux.org/index.php/PulseAudio#Pulse_overwrites_ALSA_settings)

---

