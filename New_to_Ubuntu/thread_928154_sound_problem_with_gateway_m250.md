---
title: "sound problem with gateway m250"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by ~jonathan~ on 2008-09-23
Let me start off by saying I am very new to linux but I am loving every second of it. I got everything working and looking the way I want it except for my sound. I have google this and found some information but nothing that will fix this. I ran "asoundconf list" and it came back with "Names of available sound cards:
ICH6" I then looked on the ALSA website and that card is supported with the intel chipset so I don't know or understand exactly what the problem is. If someone could shed some light on this for me and maybe step by step if you could it would be greatly appreciated, other then this small problem I love linux i have yet to find a need to boot in to xp :) also im running ubuntu 8.04 on a gateway laptop m250 if that helps any.

~jonathan

---

### Post by markbuntu on 2008-09-23
Try my guide. If the answer isn't there, it is most likely in one of the links:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

And it is step by step by step by step.....until by the end you are an Ubuntu sound expert.

---

### Post by ~jonathan~ on 2008-09-24
Thank you for that like it was helpful and I have an idea now of what needs to be done. I followed this link ( [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845) ) because it seems to be more along the lines of my problem but when I enter  "cat /proc/asound/card0/codec#* | grep Codec" into the terminal it comes back with "cat: /proc/asound/card0/codec#*: No such file or directory" and i dont know where to go from there because the list given on that page says nothing about a intel ICH6. Ubuntu is seeing my hardware in the sound preference panel the sound just isnt making it to my speakers I think.   

~jonathan

---

### Post by markbuntu on 2008-09-24
Look in this thread, post number 2:

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by ~jonathan~ on 2008-09-24
So it would be any one of these ATI SB450, SB600, RS600,VIA VT8251/VT8237A,SIS966, ULI M5461? And then one of the modules that corispond with the codec? Thank you for all your help so far it shows how much better the linux comunity over some others, you have very open arms.

~jonathan

---

### Post by ~jonathan~ on 2008-09-26
Can anyone help? this is a very annoying problem.

~jonathan

---

### Post by ~jonathan~ on 2008-09-27
Does anyone know how to fix this im a complte beginger and am not wanting to go back to windows just for sound.

---

### Post by ready4thebreak on 2008-09-27
I'm fairly new to linux myself, so I'll help you as much as I can and we'll see what happens, I won't do anything irreversible. 

First is there a speaker icon in the top panel? If so, right-click it and go to properties. There should be a pull down menu, so press. After you press it, tell me what it says.

---

### Post by ~jonathan~ on 2008-09-27
Ubuntu sees my sound card fine and all the stuff that should be there it shows intel ich6 

when I go to edit 
```
gksudo gedit /etc/modprobe.d/alsa-base
```

I dont know what model to use for 
```
options snd-hda-intel model=modelname
```

the module for the intel ICH6 are
```
 Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
		ATI SB450, SB600, RS600,
		VIA VT8251/VT8237A,
		SIS966, ULI M5461

```
from what this link says [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)  so really all I think I need is the model that corresponds with the modules listed but I cant find them anywhere and thats where i'm getting very confused. Thank you for the help.

~Jonathan

---

### Post by markbuntu on 2008-09-27
Well getting the right module loaded for you Intel HDA sound device is sort of a hit or miss thing. You just have to try them. Type aplay -l in a terminal and let's see what it says.

---

### Post by ~jonathan~ on 2008-09-27
I think if more people know how helpful the linux community was it would be ready for the masses. Back on topic when I use aplay -l this is what comes back.
```
jonathan@jonathan-laptop:~$ aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by ~jonathan~ on 2008-09-27
double post

---

### Post by markbuntu on 2008-09-27
Ok, well it seems that your card is being detected and aplay is ready to use it. let's see which module alsa is trying to use with it. Try

cat /proc/asound/modules

---

### Post by ~jonathan~ on 2008-09-27
okay, cat /proc/asound/modules
gives me

```
jonathan@jonathan-laptop:~$ cat /proc/asound/modules
 0 snd_intel8x0

```

---

### Post by markbuntu on 2008-09-27
OK, this is what the ALSA-Configuration database has to say about that:
```

Module snd-intel8x0
  -------------------

    Module for AC'97 motherboards from Intel and compatibles.
			* Intel i810/810E, i815, i820, i830, i84x, MX440
				ICH5, ICH6, ICH7, ESB2
			* SiS 7012 (SiS 735)
			* NVidia NForce, NForce2, NForce3, MCP04, CK804
				 CK8, CK8S, MCP501
			* AMD AMD768, AMD8111
			* ALi m5455

    ac97_clock	  - AC'97 codec clock base (0 = auto-detect)
    ac97_quirk    - AC'97 workaround for strange hardware
		    See "AC97 Quirk Option" section below.
    buggy_irq     - Enable workaround for buggy interrupts on some
                    motherboards (default yes on nForce chips,
		    otherwise off)
    buggy_semaphore - Enable workaround for hardwares with buggy
		    semaphores (e.g. on some ASUS laptops)
		    (default off)
    spdif_aclink  - Use S/PDIF over AC-link instead of direct connection
		    from the controller chip
		    (0 = off, 1 = on, -1 = default)

    This module supports one chip and autoprobe.

    Note: the latest driver supports auto-detection of chip clock.
    if you still encounter too fast playback, specify the clock
    explicitly via the module option "ac97_clock=41194".

    Joystick/MIDI ports are not supported by this driver.  If your
    motherboard has these devices, use the ns558 or snd-mpu401
    modules, respectively.

    The power-management is supported.

Module snd-intel8x0m
  --------------------

    Module for Intel ICH (i8x0) chipset MC97 modems.
			* Intel i810/810E, i815, i820, i830, i84x, MX440
				ICH5, ICH6, ICH7
			* SiS 7013 (SiS 735)
			* NVidia NForce, NForce2, NForce2s, NForce3
			* AMD AMD8111
			* ALi m5455

    ac97_clock	  - AC'97 codec clock base (0 = auto-detect)

    This module supports one card and autoprobe.

    Note: The default index value of this module is -2, i.e. the first
          slot is excluded.

    The power-management is supported.
AC97 Quirk Option
=================

The ac97_quirk option is used to enable/override the workaround for
specific devices on drivers for on-board AC'97 controllers like
snd-intel8x0.  Some hardware have swapped output pins between Master
and Headphone, or Surround (thanks to confusion of AC'97
specifications from version to version :-)

The driver provides the auto-detection of known problematic devices,
but some might be unknown or wrongly detected.  In such a case, pass
the proper value with this option.

The following strings are accepted:
    - default	Don't override the default setting
    - none	Disable the quirk
    - hp_only	Bind Master and Headphone controls as a single control
    - swap_hp	Swap headphone and master controls
    - swap_surround  Swap master and surround controls
    - ad_sharing  For AD1985, turn on OMS bit and use headphone
    - alc_jack	For ALC65x, turn on the jack sense mode
    - inv_eapd	Inverted EAPD implementation
    - mute_led	Bind EAPD bit for turning on/off mute LED

For backward compatibility, the corresponding integer value -1, 0,
... are  accepted, too.

For example, if "Master" volume control has no effect on your device
but only "Headphone" does, pass ac97_quirk=hp_only module option.

```
That is probably far too much information for you but, we now at least have a clue.

Try this, edit the file ect/modprobe/alsa-base and add the line:

option snd_intel8x0 ac97_quirk

to the end of it. If that doesn't work, you can try the other options but that usually fixes about 90% of the problems with the AC'97.

---

### Post by ~jonathan~ on 2008-09-28
When I use 
option snd_intel8x0 ac97_quirk
I still have no sound.

---

### Post by markbuntu on 2008-09-28
You may need to try

option snd_intel model=ac97_quirk

I am not so sure about how to get those options working but this may do it. Also, after you reboot, go back to the beginning of the guide:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

IF anyone has one of these particular machines, we could use some help here.

---

### Post by ~jonathan~ on 2008-09-28
Using option snd_intel model=ac97_quirk didnt do anything either, I dont know if this helps any but the media controls work like muting and unmuting and changing the volume all work from the hardware controls this laptop has on it.They worked from a fresh install before all this tinkering.Thank you for all the help so far im slowly getting a hang of the terminal now lol.

---

### Post by powerbookluv111 on 2008-10-21
[QUOTE=
IF anyone has one of these particular machines, we could use some help here.[/QUOTE]

I have a Gateway M250 and am also trying to get the sound to work under 8.04. Tried everything here, as well as everything else on the internet. No luck. Help!!!

---

### Post by powerbookluv111 on 2008-10-27
Okay, So I finally got audio working! After going through multiple possible solutions and such, I finally just got it to work. Although I cannot tell you what the exact fix was, I can tell you witch modules I have set to load and how I got them to work. My /etc/modprobe.d/alsa-base file looks in the section where you add lines beginning with "options" to set modules to load for alsa. So this is the section:


# Load snd-seq for devices that don't have hardware midi;
# Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
# non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-intel8x0 index=0

# Ubuntu #62691, enable MPU for snd-cmipci
options snd-hda-intel model=laptop
options snd-hda-intel model=gateway
options snd-hda-intel model=m2-2
options snd-hda-intel model=ref
option snd_intel8x0 ac97_quirk

It was the option snd_intel8x0 ac97_quirk module that I used that finally worked. Then, double click on the speaker icon in the tray to open The volume control.
Go to edit>preferences>
and make sure the following "tracks to be visible" are selected:
-Master
-Headphone
-PCM
-Line-in
-CD
-Microphone
-IEC958 **********important**********
-IEC958 Playback AC97-SPSA **********important**********
-PC Speaker
-External Amplifier ****the most important right here*******

A new tab "switches" should appear in the mixer. Go to it, under external amplifier, UNCHECK the box. IEC 958 should be checked.

Note that some devices such as IEC958 and IEC958 Playback AC97-SPSA may appear a little differently. Just make sure that external amplifier is unchecked and you have a "switches" section.

Also, some sort of ALSA extras may have to be installed for this (I can't remember what I installed) so, if a module won't load or something, Google around or check the forums to check what you need to install to get it.

Hope this all helps! If you have a question or something, you can PM me or whatever, I'm not fantastic with Linux yet, still learning, but I can try and offer some help.

Good luck!

---

### Post by webbpinner on 2009-03-10
I found some typos in the last post but the rest of the instruction are spot on.  The sounds card is working great now!  Thanks for all the great assistance.

replace:
options snd-intel8x0 index=0
with:
options snd-intel8x0m index=0

replace:
option snd_intel8x0 ac97_quirk
with:
options snd_intel8x0m model=ac97_quirk

---

