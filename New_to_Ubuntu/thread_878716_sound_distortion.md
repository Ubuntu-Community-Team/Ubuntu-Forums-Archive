---
title: "sound distortion"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by jwalters on 2008-08-03
All of a sudden in Hardy 8.04 my sound is becoming distorted on you tube.........sounds perfect for a while then cracky and distorted. Read through the trouble shooter stuff and reinstalled/downloaded etc. till I gave up cause nothing fixed the problem........great one minute..sucks the next.

Any help?........should I just dump the whole system and reinstall from CD?

---

### Post by ion072002 on 2008-08-03
what i did to have my sound up and running as it should was to uninstall pulseaudio, because it is vvery buggy. i am now on the regular ALSA platform and everything is ok

---

### Post by jwalters on 2008-08-03
I just did that.....it seems to help a little bit, but there is still some distortion........any other suggestions........should I just reinstall the whole OP.......or will it also be a waste of time and effort?

---

### Post by jwalters on 2008-08-03
just checked and "sound capture" in system/preferences/sound doesn't emit any sound on test but the rest do???

---

### Post by silkstone on 2008-08-03
Have you set that (and everything else) to ALSA in Preferences > Sound?

---

### Post by jwalters on 2008-08-03
yeah.....everything tests ok cept for the one above (previous post)

That one is dead.

---

### Post by silkstone on 2008-08-03
Before trying anything more drastic, make sure you have all these...

sudo apt-get install alsa-oss faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll w32codecs

(Assuming you have 32-bit Hardy.)

---

### Post by jwalters on 2008-08-04
ok I gave up and did a complete new installation of hardy from cd.......

still getting distortion and the "sound capture" segment of system/preferences/sound is not testing. The others test fine. 

All four read: alsa..advanced linux sound architecture...device reads hda nvidia (alsa mixer)

Since this is a complete install and it still doesn't test......what's up wid dat?

---

### Post by Ubuntized! on 2008-08-04
There are some compatibility problems I guess...

---

### Post by jwalters on 2008-08-04
Compatability?......with what? where? How to fix?

---

### Post by jwalters on 2008-08-04
In the sound preferences "system/preferences/sound" ....on 'sound capture' I
changed the setting to 'test sound'.....it came back all garbled so I think my problem may be with sound capture, but I'm not sure what that actually means.....nor what to do about it...........help???

---

### Post by Jack M. on 2008-08-04
"Sound capture" is for microphones, so that probably isn't related to the problem at hand. Did you also test for distortion in other applications? There's known to be a lot of problems with Firefox and sound playback in Flash Player.

---

### Post by jwalters on 2008-08-04
it seems through a reinstall to 7.10....that the sound tested perfect till I added either the recommended driver for this machine.....or Adobe flash.....

Is there a fix for flash?........you tube is what I want and I believe you must have adobe flash to use it.......

Thing is everything used to work fine till I think maybe the new firefox....

---

### Post by Jack M. on 2008-08-04
You could try running

```
sudo apt-get install libflashsupport
```

from a terminal (Applications > Accessories > Terminal, paste is Ctrl+**Shift**+V) to install a library that supposedly gets sound to work under PulseAudio. If that doesn't help, I'm not really sure :(

---

