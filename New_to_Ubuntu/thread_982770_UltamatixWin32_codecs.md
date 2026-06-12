---
title: "Ultamatix/Win32 codecs"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by JazonEsti on 2008-11-15
Kubuntu 8.04

I want to install Win32 codecs to play some mkv video. In Ubuntu 7.10 I was able to install Win 32 codecs via Automatix. But now I can't manually install Win 32 codecs because I can't create a /usr/lib/win32/ directory (using [these](ascending.wordpress.com/2007/03/05/quick-fix-install-win32-codecs-in-ubuntu-linux/) instructions, Dolphin says that it can't create the Win32 directory) nor can I install Ultamatix (I double click on the package, enter my password and after some disk activity I can't find the shortcut anywhere.) 

All I want is to be able to play mkv files with Mplayer. Can anyone help? Thanks!

---

### Post by jimmy the saint on 2008-11-15
Them's old instructions for old releases.  Add the medibuntu repository following these instructions, then in synaptic choos the by origin tab in the lower left and browse the medibuntu repository packages, choosing what you want.  It has all kinds of stuff, incluing win32 codecs, mplayer, google earth and lots more.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by JazonEsti on 2008-11-15
I tried installing the Win 32 codecs package, but I still can't play the file in Mplayer nor VLC. In mPlayer it gives the error message AO: [pulse] Failed to connect to server: connection refused. No error message in VLC. both play the file's sounds but not the video now and even before.

---

### Post by jimmy the saint on 2008-11-15
in the video player try setting the audio output to alsa

---

