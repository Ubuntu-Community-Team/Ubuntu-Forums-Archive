---
title: "help with sound"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by hotcarl on 2008-09-09
Hey Everyone

I have a little problem regarding sound when it comes to my Ubuntu setup.  It seems as though sound only plays from the 1st program that I open.  Any subsequent program that I open will startup muted and I cannot seem to get the 2nd program to have sound unless I quit both programs and re-start the one I want to hear.  For example, I will use wine to play WOW.  Sometimes I want to connect to my sirius online account, listen to music on my HD, or connect to ventrilo but I cannot hear the sound from any of these until I close WOW and the app it is I wanted to listen to, and then re-open the app.  Is there any way to change this?  Thanks alot for any help.

---

### Post by hotcarl on 2008-09-26
bump....please I really need help with this

---

### Post by ymra on 2008-09-26
I am not sure that this will fix your problem.  Try clicking on system at the top of the screen.  Then Preferences below that and finaly Sound.

Set everything to alsa.  

I was having issues that sound simular and that fixed them.

---

### Post by kansasnoob on 2008-09-27
Following this tutorial for 8.04 Hardy solved all my pulse audio problems:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

If you're using anything other than Hardy give a shout.

---

### Post by davidryder on 2008-09-27
System|Preferences|Sound

Change all settings from PulseAudio to ALSA (my choice) or OSS. Open a terminal and type

```
killall pulseaudio
```

Close your applications and restart them - everything should be ok. I had this same problem!

---

### Post by jackal55 on 2008-09-27
I got sirius to play by installing the Gecko Media Player as shown in part 2 of this post (assuming you have Hardy):
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by markbuntu on 2008-09-27
You cna follow my guide here. It is quite extensive and longwinded but it will fix your problem. You can start at the Multiple Application Sound Sharing Section. Be sure to at least check out the links, especially this one that has info on wine and other applications in Pulse Audio:


[http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

---

