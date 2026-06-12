---
title: "two apps open at once"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by anemptygun on 2008-05-27
I have noticed that when I have two applications open at once that use the sound I cannot play sound in one. Even if the other is paused at the moment, I actually have to close out the application to hear sound in the other. Is there a way around this, or is this unavoidable?

---

### Post by ingrid_ozikem on 2008-05-27
There is a way around this if this is a conflict between Firefox and other music programs.. the buzzwords are that this is a conflict between Pulseaudio that flash programs use and ALSA that other music programs use. One of'em locks up the sound card.. but there is supposed to be some sort of mixer that merges streams from different applications.

There was one thread somewhere which addressed this very well but I can't find it anymore.. but here are some others. Try searching for pulseaudio, firefox etc (or whatever programs are giving you a problem.)

[http://ubuntuforums.org/showthread.php?t=790634&highlight=pulseaudio+firefox](http://ubuntuforums.org/showthread.php?t=790634&highlight=pulseaudio+firefox)

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

[http://ubuntuforums.org/showthread.php?t=803959&highlight=firefox+sound](http://ubuntuforums.org/showthread.php?t=803959&highlight=firefox+sound)


Do post back here if you find the good thread I found sometime ago or solve your problem..

---

### Post by bryncoles on 2008-05-27
somebody once told me you had to add 'aoss' to the command line prompt for the program to start, and then it works fine. so i added 'aoss' to all my sound based programs. so, for example, the command to boot amarok is no longer 'amarok %U', but is now 'aoss amarok %U'. audacity is no longer 'audacity' to boot, but 'aoss audacity'. i have no idea why this works, but it does for me. 

maybe try clicking system->preferences->main menu, and selecting 'properties' for your audio programs and add 'aoss' to their command prompt?

if that doesnt work, im out of ideas!

---

### Post by hyper_ch on 2008-05-27
you first have to install aoss and then it is aimed at programs that still use oss.

---

### Post by bryncoles on 2008-05-27
thank you for the clarification hyper_ch! ;-)

---

### Post by hyper_ch on 2008-05-27
wow/wine and teamspeak2 use aoss... so with using aoss it works wonderful ;) the wow install guide on [https://wiki.ubuntu.com](https://wiki.ubuntu.com) tells you how to install aoss and how to use it.

---

### Post by Adolphian on 2008-05-27
im still sadly having problems in getting this to work :(

---

### Post by anemptygun on 2008-08-02
thanks for the suggestions guys

---

