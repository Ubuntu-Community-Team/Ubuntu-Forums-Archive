---
title: "Flash using different audio output from system"
date: 2011-09-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by psychokilla on 2011-09-05
I have a problem with my Oneiric and my soundcard output. I have internal audio on my laptop and I have a usb headset that I use.

I have disabled the onboard soundcard in the audio control panel and use my usb headset at night to listen to music/watch films/etc but when I try to watch a video from youtube the sound is played through my speakers, even though my default audio output is set to the usb headphones and the onboard audio output is, supposedly, disabled.


Any ideas?

---

### Post by mundigranja on 2011-09-10
I have that issue too. In ArchLinux is necesary to install  *lib32-alsa-plugins* and *lib32-libcanberra-pulse* but in Ubuntu I don't know what is the solution.

---

### Post by mundigranja on 2011-09-10
I found a solution by installing the[ Flash Player 11 Release Candidate]("http://labs.adobe.com/downloads/flashplayer11.html") 64-bit from Adobe.

[URL="http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11/flashplayer11_rc1_install_lin_64_090611.tar.gz"]http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11/flashplayer11_rc1_install_lin_64_090611.tar.gz
[/URL]
Download the installer and extract it on ~/.mozilla/plugins

It's all. Works like a charm on Firefox and Chrome/Chromium.

:)

---

### Post by psychokilla on 2011-09-25
Fault seems to be fixed in beta 2 :)

---

