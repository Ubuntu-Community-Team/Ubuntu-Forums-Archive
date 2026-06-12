---
title: "Aumix (and sound in general) not working."
date: 2008-07-18
forum: New to Ubuntu
---

### Post by UltraCheese on 2008-07-18
I'm not sure what happened, but it seems sometime overnight aumix stopped working.  I had recently installed updates but it was working afterwards.  Now all I get when I try to use it is a message saying "aumix:error opening mixer".  I tried installing other programs to control the audio like cam, but none of them seem to work.  I'm sure it's not a hardware problem though; I booted into Knoppix and the sound was working there.  Any ideas on what the problem could be?

---

### Post by Cone on 2008-07-19
What does ```
aplay -l
``` give you?

---

### Post by UltraCheese on 2008-07-19
aplay: device_list:205: no soundcards found...

---

### Post by UltraCheese on 2008-07-19
Just did a lspci -v and got

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Gateway 2000 Unknown device 7201
	Flags: bus master, fast devsel, latency 0, IRQ 9
	Memory at 701c0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

among the listed items.  So it seems my sound card is being recognized, but access is denied?  Is there anyway to fix this?

---

### Post by iaculallad on 2008-07-19
On your terminal, post whatever this command displays:

```
asoundconf list
```

---

### Post by UltraCheese on 2008-07-19
I get nothing.

---

### Post by Cone on 2008-07-19
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Running through that might solve your problems.

---

### Post by UltraCheese on 2008-07-19
I tried [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449), but when I got to step 3 it said to go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for my soundcard manufacturer in the dropdown box, but all that's there is a directory that leads to [http://www.alsa-project.org/alsa-doc/alsa-lib/](http://www.alsa-project.org/alsa-doc/alsa-lib/).  And to the best of my knowledge that seems completely unrelated.

Edit:  Found the correct page, continued following the steps, and everything worked.  Thanks everyone who posted.

---

