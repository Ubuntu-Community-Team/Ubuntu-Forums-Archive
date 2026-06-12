---
title: "Realtec AC97 isn't working with 12.04"
date: 2013-04-24
forum: New to Ubuntu
---

### Post by agemini68 on 2013-04-24
I have a built in soundcard that uses realtek ac97, works nicely with ubunto 10.10, but when I use 12.04, I have no sound. Is there a simple fix? I checked the mute button and everything, no sound at all. In 10.10 it tells me Internal Audio Analog stereo duplex, in 12.04, I get dummy. Step by step is the best. Is there a way to carry the driver used in 10.10 over to 12.04?

* Solved: Go into terminal, type in "alsamixer". when the panel comes up, select F6 to select sound card. Change from generic to whatever is listed below that, then reboot.

---

### Post by agemini68 on 2013-04-24
Here is some more information about it here: [http://www.alsa-project.org/db/?f=817573c2d6231af33aa611657235a1acb4a558dd](http://www.alsa-project.org/db/?f=817573c2d6231af33aa611657235a1acb4a558dd), I have tried going into the bios and disabled the front panel audio, that didn't work. I also have a Gateway 560GE.

---

### Post by agemini68 on 2013-04-24
I'm getting a little closer I made an error, so I have a realtek ALC880, I found a linux driver for it, but it is a tar bz2 file and I have no clue how to install it.

---

