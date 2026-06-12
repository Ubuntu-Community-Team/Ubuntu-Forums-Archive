---
title: "Can only get front speakers to work in Alsa"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by boyturtle on 2008-08-25
Trying to listen to Amarok through my soundblaster 5.1 in version 8.04 and can only get sound on the front set, the rear set are putting out a big fat nothing...

I have vmware installed on the machine and when I play winamp in windows, the sounds work in all channels, so I think that the issues lies in alsa setup

I had the same problem before on an earlier version and was to correct it by fiddling with the settings in alsa. I kept a record of the settings and try to apply them to the current install, to no effect

Am I missing something here?

---

### Post by phidia on 2008-08-25
If you open sound from preferences or just right click on the speaker symbol and open volume control how many speaker channels are shown there?

---

### Post by boyturtle on 2008-08-25
Only 2 channels are showing

---

### Post by phidia on 2008-08-25
There are some options you could compile alsa from source. There a section in the sound trouble shooting guide [here]("http://ubuntuforums.org/showthread.php?t=205449") on how to do that.
The other options are to install [pluse audio]("http://ubuntuforums.org/showthread.php?t=776739&highlight=speakers") and read through the [Ubuntu sound wiki]("https://help.ubuntu.com/community/Sound").

---

