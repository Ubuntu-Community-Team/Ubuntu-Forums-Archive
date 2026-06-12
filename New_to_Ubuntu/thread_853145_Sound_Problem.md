---
title: "Sound Problem"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by jnmykn on 2008-07-08
Hello All

Am fairly new to Linux/Ubuntu, installed it as a dual boot on my Asus laptop about a month ago.  Been using it reasonably constantly since then.  Mostly with the Gimp application. 
 
Yesterday I tried to play back an MP3 track - no sound.  Did a bit of investigating and basically when using Ubuntu there are no sounds from any applications.  The other partition which has windows will play back sounds so am fairly sure the hardware is OK.  It must be something within Ubuntu that is causing the problem of no sound anywhere.

My question is where to look?  What to do first?  Are there threads or FAQs or something on this that I have missed.  Thanks for any steers, but if its in anyway technical please try to think down to my level :-)

All the best  -  John

---

### Post by AOZ on 2008-07-08
theres a few things you can check

1. goto System>Admin>Hardware testing and see if any sound works
2. goto System>Preferences>Sound and clcik on the test buttons. whichever deosnt work, fiddle aroudn with the options
3. goto System>Admin>Synaptic and dowload GNOME ALSA mixer GUI. From this program you can configure a variety fo sound properties

---

### Post by appi2012 on 2008-07-08
Open the examples folder in your home folder. Try opening a .ogg file. Does that work?

What sound card do you have? Maybe ubuntu doesn't recognize it. I'm not exactly sure why sound isn't working for you, but more information would help.:)

---

### Post by jnmykn on 2008-07-08
Hi 

Thanks for the replies, that was quick.

AOZ - tried 1 and 2, before I posted, there was no sound.

Appi2012 - did as you suggested and opened a Nelson Mandela vid.  The video played OK but no sound.  I suspect Ubuntu is not recognising the soumd card.  Its a Asus laptop F3Sseries the manual that came with it doesnt mention a sound card so I am assuming its built into the mainboard (but I dont know that for a fact)  What other info would be some help?

Once again thanks for your input  -  John

---

### Post by ChameleonDave on 2008-07-08
This guide is fairly thorough:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by jnmykn on 2008-07-08
Hi Dave

The sound trouble shooting pages you suggested are about on the limit of my knowledge.  

It says go to a shell, I interpreted that as open a terminal window?  For the command aplay -l I got a list of 2 playback hardware devices -

card 0:  Intel [HDA Intel],device 0: ALC861VD Analog [ALC861VD Analog]
  subdevices: 1/1
  subdevice hash0: subdevice hash0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  subdevices: 1/1
  subdevice hash0: subdevice hash0

Not sure if the first one is a sound card or what, so I typed in lspci -v and got a whole list of things.  The one that seemed relevant was -

00:1b.0 Audio device; Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev3)
subsystem: AUSTek Computer Inc. Unknown device 1339
Flags: bus master, fast devsel, latency 0, IRQ 23
memory at Febf8000- (64 bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

I then looked for an ALSA driver via the link given.  There is no mention of the ICH8 devices.

Does this lot mean anything to you?  Is it likely there is no driver available yet.  Am getting very much out of my depth here  :-)

Best Regards  -  John

---

