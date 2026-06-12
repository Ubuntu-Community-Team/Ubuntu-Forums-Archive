---
title: "could faulty graphis driver affect login sound"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by stubblepoo on 2008-07-05
i used to have the emperors theme from star wars as my login sound which was great but having installed a proper driver for my graphics card so i can compiz-fusion the sound no longer works. in system>administrations>sound the test sound for login do not work either.

---

### Post by ZabiGG on 2008-07-05
Please install gnome-alsamixer (search for it in Synaptic) or type

```
sudo apt-get install gnome-alsamixer
```

in a terminal,

- Open the application (you'll find it in the Sound & Video menu) 
- Jack everything up and check every single checkmark
- Test again.

Should work. There is no reason why changes to your graphics settings should interfere, though. Are you sure you didn't install anything else or update?

Z.

---

### Post by stubblepoo on 2008-07-06
the overall sound has always worked, its just the login sound that doesn't. this hasn't changed that.

---

### Post by ZabiGG on 2008-07-06
I had the same problem, but I was using alsamixer instead of gnome-alsamixer, which includes more details.

Once I installed gnome-alsa mixer, I realized that some inputs weren't checked, so I checked them, and soome chanels were muted. I unmunted them.

Another thing you might want to look into, just to be sure. Look for alsa-oss and alsa-utils in Synaptic or install them via the terminal:

```
sudo apt-get install alsa-oss alsa-utils
```

to make sure you are using the latest version, restart and see if that works.

If you've installed Pulse, de-activating it might be a good idea -- it caused more problems on my system than anything else.

Z.

---

### Post by stubblepoo on 2008-07-06
alas this hasnt helped either

---

### Post by ZabiGG on 2008-07-06
Then I'm stumped. I'm sorry. The only time I had your problem was related to Pulse audio, from which I stay away religiously now...

---

