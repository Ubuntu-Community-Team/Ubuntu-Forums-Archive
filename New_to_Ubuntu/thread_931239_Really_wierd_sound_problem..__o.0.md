---
title: "Really wierd sound problem..  o.0"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Dirkzen on 2008-09-27
Hey guys :)   Having a little problem with my sound here, though its a bit odd..
My desktop has a default set of audio jacks in front, ((that i'm using now))  as well as a nice little soundcard in back I bought a while back.
(Soundblaster Audigy SE)
The trouble is.. whenever I restart, sometimes the sound comes from the front, and then the next time I restart,  it'll switch to my soundcard in back.
Its kinda frustrating, because i've found and solved this same problem from the forums here before, but I can't find it again, and I forget what the heck I did! :(
Any help would be appreciated <3

---

### Post by lucasl on 2008-09-27
If its been on the forum before, try a search. If you don't remember the title, try to remember keywords you used in the post.
(Having a more descriptive title then wierd sound problem would help in future too:))

---

### Post by markbuntu on 2008-09-27
I have written a guide to using multiple sound cards and there is a way to fix that in there. I will give you this excerpt.

Assigning Default Devices
A more common problem that often arises with multiple pci sound cards/devices is that they are not always assigned the same device number on each boot. This can result in an undesirable change in the default sound device. In order to remedy this problem we can explicitly assign the default device numbers of our sound cards by adding lines at the end of the /etc/modprode.d/alsa-base file like this:
Code:

options snd_hda_intel index=0
options snd_cmipci index=1
options snd_atiixp index=2
options snd_usb_audio index=3

This way each device will always be numbered the same. You can use aplay -l to discover your sound devices and their order.

The full guide is here:

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

