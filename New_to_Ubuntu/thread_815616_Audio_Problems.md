---
title: "Audio Problems"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by ConcreteDonkey on 2008-06-01
Hello,

I have been having trouble with my audio suddenly decideding not to work, this happens alot after watching a video on youtube or any kind of flash content, so I decided that maybe pulseaudio was having a problem after killing it, then restarted it pulseaudio give out the following errors:

```

ALSA lib conf.c:3952:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM surround71:0
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0"): initialization failed.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
 Error opening PCM device hw:0: Device or resource busy Error opening PCM device hw:0: Device or resource busy Error opening PCM device hw:0: Device or resource busy

```

I'm thinking that if I fix this problem it may resolve the audio stopping, it seems so far the easiest way to get my audio working again is to restart.

Thanks for your help in advance,

---

### Post by SunnyRabbiera on 2008-06-01
did you try just plain old logging out?
stuff like this can happen with pulseaudio I heard, its quite experimental

---

### Post by ConcreteDonkey on 2008-06-01
Logging out and in again does work, although it can still be rather annoying having to close all of my applications and open them again to get something as simple as audio working.

---

### Post by iaculallad on 2008-06-01
Try to install libflashsupport and restart.

```
sudo apt-get install libflashsupport
```

---

### Post by ConcreteDonkey on 2008-06-01
Thanks for the help, although I can't seem to reproduce the problem as it happens very randomly. I am also wondering if there is also a way to stop flash crashing firefox? or is it just that adobe is quite lazy with the development?

---

### Post by iaculallad on 2008-06-01
> **badboy4life said:**
> Thanks for the help, although I can't seem to reproduce the problem as it happens very randomly. I am also wondering if there is also a way to stop flash crashing firefox? or is it just that adobe is quite lazy with the development?

What version of firefox are you currently using?

---

### Post by ConcreteDonkey on 2008-06-01
I'm using Firefox 3 Beta 5, although since I'm dual booting with windows I am fully aware Firefox RC1 is available and I am unsure why ubuntu does not want to update firefox.

---

### Post by iaculallad on 2008-06-01
Try following the procedures below to fix your FF3:

-Download [nspluginwrapper]("http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb") and Install it.

-Install libflashsupport

```
sudo apt-get install libflashsupport
```

-On your terminal, run the following commands:

```
sudo apt-get remove --purge flashplugin-nonfree
```

```
sudo apt-get install flashplugin-nonfree
```

Close all running FF windows. Restart Firefox.

---

### Post by iaculallad on 2008-06-01
And as for the sound problem, try to navigate System->Preferences->Sound, On the "Device" tab, try to change all "AutoDetect" to "ALSA".

---

### Post by ConcreteDonkey on 2008-06-01
I have tried the fixes you have suggested in the first post and flash seems to be alot more stable after watching around 10 different youtube videos. I have also changed all of the sound settings and it seems to be working fine but as I have said before it is hard to reproduce the problem.

Also one last question, I will watch alot of videos streaming with flash in full screen, but when I am in full screen the controls seem to "lag" for example I would push the pause button and then 10 seconds later the video will pause, but if I go out of full screen it will work perfectly.

EDIT: It seems that flash is still crashing my browser

---

### Post by iaculallad on 2008-06-01
> **badboy4life said:**
> Also one last question, I will watch alot of videos streaming with flash in full screen, but when I am in full screen the controls seem to "lag" for example I would push the pause button and then 10 seconds later the video will pause, but if I go out of full screen it will work perfectly.

EDIT: It seems that flash is still crashing my browser

You could try [GNASH]("http://www.gnu.org/software/gnash/") or try reinstalling [FLASH]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash") and see the difference when trying to view youtube movies in fullscreen mode.

---

### Post by ConcreteDonkey on 2008-06-01
Thanks for all of the help, although I think that I will just have to run Windows XP through VirtualBox and watch the videos through there.

---

