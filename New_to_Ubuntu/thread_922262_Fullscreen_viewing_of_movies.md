---
title: "Fullscreen viewing of movies"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by audreymac on 2008-09-17
Vlc player has been installed, when I to play a dvd sometimes it works, other times no.
The picture is centred but its not possible to extend it to cover the whole screen.
The same with audio - not reliable at all.
Is this fixable??
Thanks in advance.

---

### Post by Bakon Jarser on 2008-09-17
Maybe this guide can help.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Orange_and_Green on 2008-09-17
A heartfelt hello to you and to beautiful Ireland:)

I had a similar problem with my wife's laptop, which boiled down to the fact that hardware was badly supported. A few things that come to mind:

Video: 1) Do you know what model your video card is? And what driver you are using?
       2) You could experiment with VLC's Settings->Preferences.
          Check "Advanced Options". Select Output modules, try "OpenGL", "X11" and "XVideo", and see if any of these gets it better. Also, try enabling "Alternate fullscreen method" under X11/XVideo/OpenGL/whatever you have, hopefully one if the combinations may work better...
       3) You mentioned that playing DVDs sometimes fails... did you install libdvdcss2 from Medibuntu (instructions AND LEGAL NOTES [here]("https://help.ubuntu.com/community/Medibuntu"))?

Audio: Could you give any hardware info on this one?

Wish you the best of luck:KS

---

### Post by audreymac on 2008-09-17
Thanks for the quick replies and welcome.
I will try the instructions from you both later and hopefully solve this glitch.
From audreymac in, at the moment, sunny Ireland.

---

### Post by joyson20 on 2008-09-17
ogle player is a good option for playing dvd's

---

### Post by audreymac on 2008-09-20
Video/fullscreen now possible using gnome player. Grateful thanks.
Just one problem in relation to audio .  
How to rectify this message-
gnome player error - failed to open/tmp/<head>.
when I am trying to listen to live radiostreams.

---

