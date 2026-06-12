---
title: "Popping noise on reboot"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by shourdad on 2012-07-17
Hi,

I'm fairly new to linux and Ubuntu, having just installed the latest version onto my HP DV6 (alongside Windows 7). 

Whenever I shut down or reboot, there is always a loud pop/crack noise  from the speakers just before it turns off. It doesn't happen when I reboot from Windows though. I'm worried that the sound may be damaging my speakers.

I've searched around for solutions and none of the ones I've found seem to be relevant anymore since they are relatively old.

I tried this solution below but to no avail.  I'm sure I did it correctly.
> 
Open terminal and do:
  Code: gksudo gedit /usr/lib/pm-utils/power.d/intel-audio-powersave Find this line:
  INTEL_AUDIO_POWERSAVE=${INTEL_AUDIO_POWERSAVE:-true}   and comment it out by putting a "#" in front of it like this:
  # INTEL_AUDIO_POWERSAVE=${INTEL_AUDIO_POWERSAVE:-true}   Just below this line you make a new line, like this: 
  INTEL_AUDIO_POWERSAVE=false   So now you will have:
  # INTEL_AUDIO_POWERSAVE=${INTEL_AUDIO_POWERSAVE:-true} INTEL_AUDIO_POWERSAVE=false   Save the file (File > Save) and exit.
  Reboot the computer.
  The popping sound will be gone.
  NOTE: If you for some reason need to undo the setting, just open the file again and remove the "#" from:
  INTEL_AUDIO_POWERSAVE=${INTEL_AUDIO_POWERSAVE:-true}   and delete this line: 
  INTEL_AUDIO_POWERSAVE=false   Save the file.
  Reboot.
Any help would be greatly appreciated.

---

### Post by Redblade20XX on 2012-07-17
Maybe this will help:
[https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#Pops_When_Starting_and_Stopping_Playback](https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#Pops_When_Starting_and_Stopping_Playback)

- Red

---

### Post by shourdad on 2012-07-18
Sorry to be a pain, but I don't fully understand how to change the parameters. Are you able to assist me here?

Thanks

---

### Post by NikTh on 2012-07-18
Hi , 
you can try some tricks and see what happen. 

```
echo "options snd-hda-intel power_save=0" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
Reboot and see if fixed. If not , then try another 
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
``` and 
find the line you added before [B]options snd-hda-intel power_save=0 and make it like this 
options snd-hda-intel power_save=0 power_save_controller=N .[/B] Save the file and reboot. Those are from site** @Redblade20XX **gave you.If nothing from above tricks worked , you can try alsamixer. 
Open a terminal and write ```
alsamixer
``` , try to find something** about Line **and if its muted [MM] un-mute it by click "m" key. With arrows (up-down) you can volume-up or volume-down, or if its un-muted then mute it with "m" key. 
Thanks

---

### Post by audiomick on 2012-07-18
I would suggest, rather than simply changing lines, to comment them out and add new ones, as well as comments about what you have done. A # at the start of a line denotes a comment, i.e. that line will not be read as part of the config file. You would end up with something like this

```
line of code
another line of code
another line of code
#old line that has been changed
#short explanation of what you did like
#this is what I changed
new line of code
```

This is generally a good practice if you want to start manually changing config files and such like. It is also a good idea to save a copy of the file to somewhere else before you start messing around with it. ;)

---

### Post by shourdad on 2012-07-18
I've tried both tricks that Redblade20xx posted but unfortunately neither of them work.

Looking at the alsamixer I've got 6 options: Master, Headphone, Speaker, PCM, Mic Jack Mode (which can have either [Mic In] or [Line In]) and Beep. I played around with muting/unmuting the different options but none of them seemed to work also.

---

### Post by audiomick on 2012-07-18
> **shourdad said:**
> I played around with muting/unmuting the different options but none of them seemed to work also.

Yeah, the only thing that has a chance of working is perhaps muting the output, but whether that will help or not depends on where the pop is happening. I did have that problem on this machine a while back. I don't actually know if it solved or not. What changed is that I got a new pair of monitors without internal speakers and then a set of external speakers. The speakers only get turned on when I specifically want to listen to something, and are usually off when the computer gets started or shut down, so I can't say for sure that the pop is gone or not. 

As I said, try muting the speakers before you shut down, or turning them down all the way. It is not a solution, but if it helps, you wont have the worry of damage to the speakers (which is justified to an extent).

---

### Post by SmallWorld on 2012-09-15
If you're still dealing with the popping noise (or anyone still dealing with this problem):

I had the same problem on a HP dv6-6140us.  After booting or unsuspending my computer while on battery power, the speakers would make a regular clicking / popping / cracking sound.  After reading other postings I realized that this only occured when I was running Chrome and left certain websites open such as GMail.

Rather than mess Ubuntu's speaker settings, I followed the solution at [http://ubuntu-with-wubi.blogspot.com/2012/07/weird-clicking-noise-in-chrome.html]("http://ubuntu-with-wubi.blogspot.com/2012/07/weird-clicking-noise-in-chrome.html") which is to disable the PepperFlash plugin in Chrome.

After disabling the PepperFlash plugin, Chrome is still able to view Flash-powered pages just fine.  And the noise is totally gone.

---

### Post by s1baker on 2012-09-15
I had a popping noise on my system for a while ( started happening just after I installed my new wireless router).
Moved the router away a little bit and the popping sound went away.
Don't know anything about routers, just thought I would throw this in.

---

### Post by M3m3nt0 on 2013-09-08
I have the same problem on a HP Pavilion DV5-1110el with Ubuntu 12.04.3 64bit.

anyone has got a solution?

---

### Post by M3m3nt0 on 2013-09-09
I think I found a solution!! :D

I've upgraded the Alsa driver to the latest daily build using this procedure: [Upgrading Alsa / DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

no more crackling sound at power off/reboot!!

---

