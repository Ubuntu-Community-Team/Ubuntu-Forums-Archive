---
title: "Sound playback problem - after playing music, can no longer stream via firefox"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by TMcKSmith on 2008-06-09
After playing music in Banshee, Amarok, Rythmbox, etc. I cannot get sound playback in my browser (youtube, etc.) until I restart my computer.  Any help would be appreciated.

---

### Post by Cypher on 2008-06-09
Have you tried closing the other music applications before trying Firefox? Also, if you re-open the music apps does the sound still play?

---

### Post by llama320 on 2008-06-09
this is a very common problem for hardy

If your problem was to do with flash, install libflashsupport and reinstall flashplugin-nonfree

```

sudo apt-get install libflashsupport
sudo apt-get install --reinstall flashplugin-nonfree

```

then go to System > Preferences > Sound and change all "sound playback" areas to pulseaudio. Then, if your music player has this functionality, change its output engine to pulseaudio.

Then just restart..that did it for me

If that doesn't work, just check the forums, it's been rather well documented

---

### Post by realstraw on 2008-06-09
Try
```
killall pulseaudio
```

---

### Post by TMcKSmith on 2008-06-09
> **llama320 said:**
> this is a very common problem for hardy

If your problem was to do with flash, install libflashsupport and reinstall flashplugin-nonfree

```

sudo apt-get install libflashsupport
sudo apt-get install --reinstall flashplugin-nonfree

```

then go to System > Preferences > Sound and change all "sound playback" areas to pulseaudio. Then, if your music player has this functionality, change its output engine to pulseaudio.

Then just restart..that did it for me

If that doesn't work, just check the forums, it's been rather well documented


thanks.  this seemed to work

---

