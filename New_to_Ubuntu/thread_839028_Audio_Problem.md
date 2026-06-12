---
title: "Audio Problem"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by Samurai Penguin on 2008-06-24
HI,

in need of some help please. Have a SB Audigy card installed and worked ok
until I installed some codecs and then the audio stopped working on the
Audigy output.
However, if I plug into the rear panel audio (on-board audio) it works
just fine. Any ideas? Thanks ...

---

### Post by tribble222 on 2008-06-24
First I'd try running

$ sudo /etc/init.d/alsa-utils restart

To restart alsa.  If that doesn't do anything then post here the output of the following command:

$ asoundconf list

and the contents of the file .asoundrc in your home directory (/home/SAMURAI_PENGUIN/.asoundrc)

---

### Post by Samurai Penguin on 2008-06-24
Names of available sound cards:
NVidia
Audigy

I turned on "hidden files" but do not see the file you mentioned

---

### Post by tribble222 on 2008-06-24
If you don't ever want to use your onboard sound, try disabling it in the bios.  Otherwise, set the Audigy as your default sound device by running

$ sudo asoundconf set-default-card Audigy

---

### Post by Samurai Penguin on 2008-06-24
Hurray !!! Hurrah !!! It worked ... thanks for seeing it through {8 ^,

---

