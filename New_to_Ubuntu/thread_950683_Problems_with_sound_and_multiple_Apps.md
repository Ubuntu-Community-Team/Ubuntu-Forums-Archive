---
title: "Problems with sound and multiple Apps"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by Geekboy on 2008-10-17
I'm having problems with sound and multiple Apps.  I can't seem to have 2 apps play sound at the same time.  If I'm watching a divx video, then pause, I can't play an mp3 or youtube.  Or vice versa.

Any ideas?  Thanks.

---

### Post by wolfen69 on 2008-10-17
```
sudo apt-get install libflashsupport
``` then restart firefox if open.

---

### Post by ezramorris on 2008-10-17
> **wolfen69 said:**
> ```
sudo apt-get install libflashsupport
``` then restart firefox if open.

If that doesn't work, and this is specific to firefox, try [this post]("http://ubuntuforums.org/showthread.php?t=75237").

If it's not just firefox, go to system>preferences>sound, change everything to alsa, then also change your media player(s) to use alsa.

---

### Post by Geekboy on 2008-10-17
It's not really just related to flash.  It's any app.   I could be using Totem then switch to VLC.  VLC will not work.  And it goes the other way.  It seems that sound gets locked to only one app at a time.  The only way to fix it is to reboot.

---

### Post by ezramorris on 2008-10-17
> **Geekboy said:**
> It's not really just related to flash.  It's any app.   I could be using Totem then switch to VLC.  VLC will not work.  And it goes the other way.  It seems that sound gets locked to only one app at a time.  The only way to fix it is to reboot.

did you try changing everything to alsa?

---

### Post by SunnyRabbiera on 2008-10-17
This is a classic problem when concerning linux, the sound server in linux is much different then it is in windows so when you have one audio application up you may not be able to get the second one working.
The problem comes with how linux speaks to the sound card, I mean yes it can make sound work and its detection of most sound devices is pretty decent but the sound card might not understand the message.
Most sound cards are made to work mainly with windows like most devices out there, so when you have linux installed the sound card works but how linux utilizes it is set up differently so while the linux kernel is speaking plain english to the sound card, th sound card can only reply in Klingon and it only understands Klingon.
But this is being fixed with tools on the linux front that can interact with the sound card better, things like Pulse audio and OSS4 seem to be targeted to make the connection between the sound card and the linux kernel work better so you can use as many sound apps as possible.

> **ezramorris said:**
> did you try changing everything to alsa?
Indeed go up to system, then to settings and then to sounds.
There you will see a bunch of pulldown menus marked "automatic", change them all to Alsa

---

