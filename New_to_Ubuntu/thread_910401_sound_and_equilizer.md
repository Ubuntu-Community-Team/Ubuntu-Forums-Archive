---
title: "sound and equilizer"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-09-04
Hello!
My dad LOVES to listen to music, he has about 5 gb of songs form limewire, but he loves everything as far as sound goes, just perfect.

IS there any way to get an equilizer screen for him to adjust all the different ranges of sounds?

---

### Post by hyperhopper on 2008-09-06
ubumptu

---

### Post by Infinite Indefinite on 2008-09-06
Well, here's one way:

1) Install audacity (either through Add/Remove programs or via the terminal:
$ sudo apt-get-install audacity).

2) Go to System > Preferences > Sound and select ALSA for sound playback and Music and Movies.

3) Start audacity and open the file you wish to hear.

4) Go to Edit > Select > All

5) Then go to Effect > Equalization.

I hope that helps.

---

### Post by sancho panza on 2008-09-06
Which music player do you use on ubuntu? Most media players come with an in-built equalizer or have plugins that do the same job.

---

### Post by kansasnoob on 2008-09-06
You could try gnome-alsamixer:

[ATTACH]84313[/ATTACH]

[ATTACH]84314[/ATTACH]

```
sudo apt-get install gnome-alsamixer
```

---

### Post by wolfen69 on 2008-09-06
vlc and amarok also have equalizers.

---

### Post by hyperhopper on 2008-09-06
this is for my dad, and the only music player he knows how to use is limewire.....

---

