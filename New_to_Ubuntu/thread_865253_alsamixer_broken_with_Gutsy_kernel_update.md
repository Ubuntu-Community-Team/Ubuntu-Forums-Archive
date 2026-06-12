---
title: "alsamixer broken with Gutsy kernel update"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by ms_whosit on 2008-07-20
I was having some trouble with the sound, and I noticed that gnome-volume-control now uses OSS instead of alsa mixer, which it used to use. I also noticed that it only has playback controls and not capture/record controls. I think this change was caused by a recent automatic update to the kernel (2.6.22.15-generic).

When I tried to open alsamixer from the command line I get this error:

-----------------------------------------------
ALSA lib simple_none.c:1710: (simple_add1) helem (MIXER,'Master Playback Volume',0,2,0) appears twice or more

alsamixer: function snd_mixer_load failed: Invalid argument
-----------------------------------------------

I have a Dell Inspiron 1525n which came loaded with Ubuntu 7.10. The output of 
aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Conexant HSF Modem [Conexant HSF Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

One other thing is that the mixer device claims to be "Conexant HSF (OSS mixer)". (And this is the only option in the Sound Preferences settings for mixer device). I'm not absolutely certain, but it may have been STAC92xx Analog before.

To the best of my knowledge, alsamixer, and sound/recording in general, worked fine before the update. Right now, I can play sound with OSS but it has problems adjusting the volume and I don't think I can record. 

Any help would be appreciated--let me know if additional information would be helpful in diagnosing this. thanks!

---

### Post by billgoldberg on 2008-07-20
This might not be the best forum to post it in.

But still.

Press esc in the grub and boot from the old kernel.

See if the problem occurs there too.

If not, it's the new kernel.

If it isn't the kernel, you can start looking elsewhere.

I can't really help much with this.

I can suggest reinstalling ALSA or asking help in #alsa on irc.freenode.net

---

### Post by ms_whosit on 2008-07-20
thanks. I just tried this and yes, it works under the old kernel (2.6.22.14). I'll try posting about it under a different forum.

---

### Post by tipiglen on 2008-08-29
I had the same problem, and the same solution, e.g. step back one kernel.

Thanks for the suggestion.  

Should I now install OSS?

Salaam/Shalom/Shanthi/Dorood/Peace
   Namaste  -ed

---

