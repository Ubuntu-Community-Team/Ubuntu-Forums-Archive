---
title: "[SOLVED] 5.1 Surround Sound on computer"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by adobrakic on 2008-07-25
I hooked up a 5.1 surround sound system on my computer, and I was wondering if there's a program that takes advantage of it while playing music, movies, etc. This isn't really necessary, because it already sounds nice, I was just wondering.

---

### Post by bobnutfield on 2008-07-25
> **adobrakic said:**
> I hooked up a 5.1 surround sound system on my computer, and I was wondering if there's a program that takes advantage of it while playing music, movies, etc. This isn't really necessary, because it already sounds nice, I was just wondering.

Have a look at this:

[http://ubuntulinuxhelp.com/the-simple-way-to-get-51-surround-sound-audio-working-in-ubuntu/]("http://ubuntulinuxhelp.com/the-simple-way-to-get-51-surround-sound-audio-working-in-ubuntu/")

Bob

---

### Post by adobrakic on 2008-07-25
Is there a program that tests the surround sound?

---

### Post by bobnutfield on 2008-07-25
There is no program (that I know of, someone else may know of one), but you should be able to test the output with your mixer in your volume controls.  Try different volumes with the Front, left and right  with various settings in the mixer.

Bob

---

### Post by Brebs on 2008-07-25
> **adobrakic said:**
> Is there a program that tests the surround sound?
```
speaker-test -D surround51 -c 6 -t wav
```

And to play stereo music through the 5.1 speakers, see [this config file](ftp://ftp.brebs.me.uk/linux/asoundrc).

---

