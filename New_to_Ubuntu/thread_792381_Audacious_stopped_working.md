---
title: "Audacious stopped working?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Jhodas on 2008-05-12
Hi there, I'm a bit of a linux noob, so please bear with.

I've recently installed xubuntu and proceeded to try and set up a music player. audacios seemed like a good choice.

After much faffing, I managed to get it playing through the OSS mixer to my M-Audio delta 2496, however, I changed something somewhere (don't know what) and now no matter what I do, audacious wont play anything, it won't even recognise a file.

The files are coming from a NTFS partition on another HDD.
I have tried removing audacious using apt and reinstalling, but it seems to retain the same configuration (i made the font bigger).
I have tried autoremoving everything to do with audacious and reinstalling, same result.

Now no matter which audio output plugin I choose (ALSA or OSS) audacious wont even show the file information. 

I have a feeling it is something really silly, because it was playing initially. Any thoughts or help greatly appreciated.
Jho.

---

### Post by Jhodas on 2008-05-15
This appears to have solved itself... It seemed the OSS driver was simply very sluggish in deciding that it was needed.

---

