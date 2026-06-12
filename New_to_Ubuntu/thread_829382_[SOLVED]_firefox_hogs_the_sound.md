---
title: "[SOLVED] firefox hogs the sound"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by swaknight on 2008-06-14
Ok, another problem :(
I checked the other threads and have not found anything that worked.

When i have music playing in firefox 3.0, no sound comes from any other program, not pidgin, not even gnome it self. Is there a fix to this that I am missing. 

On a lighter note, I can not get it to automatically recognize headphones either, i have to do it by hand, but that is not as big of a problem

---

### Post by alienexplorers on 2008-06-14
With my sound blaster live card I have no problem hearing multiple sounds even when running firefox.  I can listen to a mp3 and still hear the audio on a youtube video.

---

### Post by adamorjames on 2008-06-14
You mean Flash? I think I know of a fix. Try this:

 [http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb](http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb)

  sudo apt-get install libflashsupport

  sudo apt-get remove --purge flashplugin-nonfree

  sudo apt-get install flashplugin-nonfree




Also if you are using mplayer make sure that you set the audio to pulse audio if it is Hardy Heron or whatever else if it is not.

---

### Post by swaknight on 2008-06-14
If that is the fix that I am thinking about, I get sound from the flash just fine. Its everything outside of firefox that wont play

---

### Post by swaknight on 2008-06-14
nevermind, it worked like a charm. thankyou

---

