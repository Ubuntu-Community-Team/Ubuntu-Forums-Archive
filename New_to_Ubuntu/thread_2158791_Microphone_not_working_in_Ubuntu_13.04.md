---
title: "Microphone not working in Ubuntu 13.04"
date: 2013-06-30
forum: New to Ubuntu
---

### Post by pjm894 on 2013-06-30
I recently installed 13.04 on my Lenovo U510 laptop, and both my internal and headphone-based mics don't work.
I made sure they were unmuted on Alsamixer. 
They register when I tap on or blow into the mics directly, but not when I speak.
Skype says there is a "Problem with Audio Capture"
Sound Recorder refuses to record at all.
Google Hangouts lets me initiate a hangout, but my partner only receives static and ambient noise.

Please help!

---

### Post by kchoff on 2013-07-30
I'm running 13.04 also and Google Hangouts is having trouble finding my mic, even though I checked that it was on in Alsamixer.

---

### Post by mbabar96 on 2013-07-30
Open terminal and paste "sudo gedit /etc/modprobe.d/alsa-base.conf", hit  Enter. It will open a file alsa-base.conf. scroll to the end of the  file and add the this "options snd-hda-intel position fix=1" or "options snd-hda-intel position index=2"

---

