---
title: "MIDI music player"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by eru777 on 2008-08-29
Hello, I tried TImididy but even if it seems to be installed I do not see it in the program list, and typing it with alt and F2 does not make it run :'( How do I run it?

PLease can you tell me of a program that works with MIDI music files (plays them, and maybe can make a playlist ) I have tried to find older threads but nothing helped me.

THanks

---

### Post by whitethorn on 2008-08-29
As far as I remember you need to use

```
timidity /path/to/file.midi
```

---

### Post by ajgreeny on 2008-08-29
If I remember correctly, timidity is just a console utility and to get a gui you need to make your own shortcut in the menu and use the command ```
timidity -ig
```.  This will give you a gnome interface.

For more information see ```
man timidity
```which gives other gui options you may prefer.

---

### Post by eru777 on 2008-08-29
IS there any way to do it under a GUI ? Any player that supports midis?

---

### Post by yoman on 2008-08-29
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by NewDisciple on 2008-08-29
If you just want a midi player with a gui try Kmid; it's in the repository.  Timidity runs from the command line (same for pmidi).  There is a midi plugin for XMMS, however this is not currently in the repository and if you are fairly new to ubuntu and linux I wouldn't want to lead you down that road.
You might also try Pykaraoke which does have a front end.  Timidity is required to be installed for this to run.  It also installs the necessary sound patches.
Anyway, your best options are kmid & pykaraoke.

---

### Post by Vivaldi Gloria on 2008-08-29
> **ajgreeny said:**
> and to get a gui you need to make your own shortcut in the menu and use the command ```
timidity -ig
```.  This will give you a gnome interface.


Unfortunately timidity from the repos gives this:

```
vivaldi@narval:~$ timidity -ig
Interface `g' is not compiled in.
```

---

### Post by eru777 on 2008-08-29
thanks all I will try it:KS

---

### Post by ajgreeny on 2008-08-29
Sorry, I forgot.  To get the ```
timidity -ig
``` to work you need to install **timidity-interfaces-extra** as well.  Then I think you will get it to work OK.  It certainly does for me.  Dont forget to install freepats as well to get the voices needed to get any sound, I think.

---

### Post by bruce89 on 2008-08-29
Certainly in Hardy and above, Totem plays MIDI files.

---

### Post by wolfie2x on 2008-08-29
yep on Hardy, "Totem Movie Player (GStreamer)" plays midi fine. I did have some trouble initially though.. can't remember exactly what I did, but now it just works fine.

(but there's still a bug where, after playing one midi file, if you try to play another file, it says 'codec not found'!. simply closing totem and trying again works; - this has already been fixed in svn I think)

---

### Post by markbuntu on 2008-08-29
Rosegarden is built to play/create/edit midi files.

---

### Post by eru777 on 2008-08-30
Nothing works except movie player, andthat works with the errors in the end, plus no playlists allowed because ofthe same error .

---

### Post by NewDisciple on 2008-08-30
I have not used a midi player in a while, but I did today.  Or I should say tried to.  I have never had a problem with any of these until today.  My experience was exactly like yours.  I'm kind of thinking that something may have been removed during an update.  Not sure though.  I will work on this and post a solution.

---

### Post by NewDisciple on 2008-08-30
Okay...got kmid working.  Open kmid go to settings.  Select MIDI Setup.  Your MIDI device is probably set on the first choice - Midi through midi Port-0-ALSA device.  Select the second choice - Timidity Timidity port 0 -ALSA device.  Do make sure that Timidity is installed first.  Should work for you.

---

### Post by eru777 on 2008-08-31
> **NewDisciple said:**
> Okay...got kmid working.  Open kmid go to settings.  Select MIDI Setup.  Your MIDI device is probably set on the first choice - Midi through midi Port-0-ALSA device.  Select the second choice - Timidity Timidity port 0 -ALSA device.  Do make sure that Timidity is installed first.  Should work for you.

Nah, doesn't work . It shows that it is playing, but no sound can be heard. Thanks though .

---

