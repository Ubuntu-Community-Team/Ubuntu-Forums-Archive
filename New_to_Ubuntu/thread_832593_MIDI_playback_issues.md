---
title: "MIDI playback issues"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by TheSeanKelly on 2008-06-17
I'm trying to run sibelius 5 (midi music notation software) in windows xp in a virtualbox virtual machine on a dell latitude d820.  Core duo processor, 2 gigs of ram, Sigmatel audio card.

The virtual machine is running XP with 192 megs of ram and 8 megs of video designated, using pulse audio as the audio driver.  

Sound playback is fine in the virtual machine, except for sibelius.  The program itself runs fine and well, but when I play something back using midi the rythm is all off...very sporadic and jumbly.  Will go very slow for a few measures then lightning speed as if to catch up.

I understand that virtual machines use the host's drivers, so I conclude this must be a problem with my MIDI in ubuntu?  Is this accurate?  Any ideas towards fixing the problem?

Thanks

---

### Post by spiderbatdad on 2008-06-17
Possibly install timidity from synaptic package manager if it is not installed. The package is buggy IMO so I would recommend removing it after installing it (lol) but gstreamer inherits the codecs somehow and continues to play midi after timidity is removed.

---

### Post by TheSeanKelly on 2008-06-17
No dice. Other thing I thought of - I'm using PulseAudio for the audio driver in the virtual box..anything else be better maybe?

---

### Post by iansane on 2008-06-18
Have you tried or do you have the option to use alsa for your VM?

And is 192 enough RAM for windows and anything else to run at the same time?
I know we can't all have tons of RAM recently I upgraded and have 2 GIGs to play with. I set my VM with XP to use 512

---

### Post by TheSeanKelly on 2008-06-18
Yeah I just tried(alsa), and I don't know but upping the ram doesn't make any difference.  I think it's plenty of ram because the virtual machine isn't running any drivers.

---

### Post by TheSeanKelly on 2008-06-18
solved!

I uninstalled virtualbox-OSE and got virtualbox puel.  Never knew there was another one besides ose..haha

thanks for help!


Though I am curious - anyone have any idea why it works in puel and not in ose?  Something different in sound handling?

---

### Post by crhylove on 2008-11-07
What are your sound settings?  Did you have to install timidity?

Thanks in advance.

---

