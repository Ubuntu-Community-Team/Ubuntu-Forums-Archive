---
title: "sound issues"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by taith on 2008-07-30
hey

having problems with my sound... only one program can play a sound at a time... have to close one, to get another to play... it didnt used to be like this untill this fresh install of hardy... :-(

in my sound preferences... if i set music/movies to pulse audio i get "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect: Connection refused"... and if i set it to OSS or ALSA i get "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application." :-(

and thats without any sound playing atall at the moment... also i should mention that all the boxes on that screen are set to pulse audio at the moment :-)

---

### Post by oliviacond on 2008-07-31
go to sound preferences, and select ALSA.

---

### Post by tuxxy on 2008-07-31
Select ALSA for movies/video and sound output in system > admin > sound

---

### Post by Superkoop on 2008-07-31
If that didn't work for you, and if you have paprefs installed, you can use that, and check the check box in the "Simultaneous Output" tab. This let me listen to audio from multiple devices.


To install it in case you don't have it yet:

```
sudo apt-get install
```

Then run it:

```
paprefs
```

---

