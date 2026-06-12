---
title: "no sound or audio"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by thehellboy on 2008-08-18
im my acer aspire 5051.. while im playin movie or audio files audio is not comin..previously audio was coming but after i installed some updates from update manager this audio probles has begun.. help me in solving this please

---

### Post by cybrsaylr on 2008-08-19
Did you try to reboot yet.
Same thing just happened to me after installing the new banshee version, I lost all audio.

After a reboot all audio can back.

---

### Post by kcoylenet on 2008-08-19
Check to see that an update to the sound function didn't set the sound to "mute." Right click on the speaker icon in the upper right of the screen. Click on "Volume Control" and make sure that the master volume out (on the left) is un-muted. If it has a red 'x' on it, click on that to un-mute.

---

### Post by thehellboy on 2008-08-20
no i restarted so many times and and sound is not muted ..but still audio is not coming..

---

### Post by Bodsda on 2008-08-20
Sometimes pulseaudio screws up, try entering this in a terminal

```
killall pulseaudio
```

then close your music player or whatever your trying to play and open it again

---

### Post by t0p on 2008-08-20
This happened to me too.  It was a pulseaudio/flash 9 issue.

The fix at [this link]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472") may sort you out.  It solved the problem for me!

---

