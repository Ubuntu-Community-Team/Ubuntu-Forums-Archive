---
title: "System Audio problem! Invalid stream"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by tictac232434 on 2008-10-07
Hey, I am currently have many problems with Audio. When I first installed Ubuntu then Installed Movie player and codec's for my audio files they all worked fine. Then I installed some updates pre-released and un-supported and then nothing has worked sound wise. I checked to make sure it was not the Movieplayer but its also the internal sound. I have tried installed/reinstalling movie player and codec's but still nothing. I might have to completely re-install Ubuntu and just beware Unsupported updates. But if anyone can help I will appreciate it.

Here is the error messages for Ubuntu when trying to play any sound at all.

Movie Player Error: "Failed to connect stream: Invalid Argument"
          
Sound Preference's In Ubuntu:
"Audiotestsrc wave=sine freg=512!  audio convert ! audiosample ! gconfaudiosink: Failed to connect stream: Invalid Argument"

Any help is appreciated if it saves me from re-installing Ubuntu and losing my history... Thank!!!!

---

### Post by Partyboi2 on 2008-10-08
Have you tried going to sound options (System>Preferences>Sound) and changing to alsa?
I came across [COLOR=Blue][this bug report]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/191027") [/COLOR] that has a few suggestions, might be  a good read.

---

