---
title: "Natty How To: Audio over HDMI for NVidia"
date: 2011-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Hedgehog1 on 2011-04-27
This is a quick how-to showing the setup of audio over HDMI for NVidia cards in Natty using only GUI.  

**NOTE: You will need to have the NVidia Restricted Video Driver loaded to support Audio over HDMI for NVidia cards.**

Step 1: Start Banshee (or your audio player of choice) playing music. *When we hear the music, we will know the Audio Setup is correct.*

Step 2: Startup System Settings. If you are in Unity, you can do this two ways (1) using the System Settings icon in the launcher or (2) selecting the option in the logon menu.

[IMG]http://img703.imageshack.us/img703/5583/nattyaudio01.png[/IMG]

Step 3: Select 'sound' in the hardware section:

[IMG]http://img34.imageshack.us/img34/2077/nattyaudio02.png[/IMG]

Step 4: In the 'Output' tab, select the output with 'HDMI':

[IMG]http://img684.imageshack.us/img684/6799/nattyaudio09.png[/IMG]

Step 5: In the 'Hardware' tab, select the hardware with 'HDMI':

[IMG]http://img824.imageshack.us/img824/3812/nattyaudio03.png[/IMG]

Step 6: Using the profiles list, select each one until you hear music (The: **Digital Stereo (HDMI) nr 4 Output** is typically the active one):

[IMG]http://img35.imageshack.us/img35/1980/nattyaudio04.png[/IMG]

Step 7: (Optional) Once music is playing over HDMI, you can turn off the analog audio if you want. *Some folks have reported they must turn off the analog audio to allow the volume control to function properly*:

[IMG]http://img822.imageshack.us/img822/7594/nattyaudio11.png[/IMG]

***The Hedge***

:KS

---

### Post by dino99 on 2011-04-28
nice post, but quite useless here, better to post it into subforum: tutorials & tips

---

### Post by Flymo on 2011-08-19
Nice post, indeed! Very clear.
 
Thanks for that - we still do not have audio over HDMI, but suspect that is more to do with Natty - and the older nVidia driver we are forced to use. <sigh> ;)

Same machine (EMachines ER1401, AMD K325 + nVidia 9200) works fine in other distros, wish we knew why.

The only options we are offered in 'Hardware' and 'Output' are the 'Profiles' in Hardware, and even then that's only HDMI output or HDMI output with analogue input.  

NB: There's a third way to get to 'Sound Preferences' - click on the speaker icon in the top bar.

Unity is still a minefield - it's possible to move about, but the route is often tortuous.

All the best, Ben

Edit: This is the output of <aplay -l>

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

We are using the nVidia version 173 driver since the 'Version Current' falls over before login. :(

---

