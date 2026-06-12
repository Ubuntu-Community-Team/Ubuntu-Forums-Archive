---
title: "HOWTO: the right soundcard with mozilla-plugin-vlc"
date: 2006-01-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Denis on 2006-01-11
*I thought someone may be interested to read this in the future, so they don't have to spend time to find the solution.*

This howto is for people who use the VLC plugin to see video with Firefox. 

It appears that the plugin doesn't use the same audio settings as VLC (the program). The plugin always uses OSS. This means that if you set your audio properties for any other audio system (like ALSA e.g.), they will not be used by the plugin. This can be a problem when you have more than one soundcard. You will have no sound with the plugin. 

This can be fixed easily by setting up OSS in VLC. 
Go to preferences > audio > output modules > OSS
Set the correct OSS device (/dev/dsp1 e.g.)

Enjoy your video.

---

