---
title: "How do I get my microphone and headphones to work?"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by smiley07 on 2011-09-09
I have a Toshiba Satellite L655, and the built-in microphone, microphone input jack, and headphone output jack don't work.

I think I may have found a solution, but I don't understand it. I found it here: [http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

It says to edit:  /etc/modprobe.d/alsa-base.conf and add:

```
options snd-hda-intel model=thinkpad
```I don't know how to do this. Can someone help me?

---

### Post by Ms_Angel_D on 2011-09-09
> **smiley07 said:**
> I have a Toshiba Satellite L655, and the built-in microphone, microphone input jack, and headphone output jack don't work.

I think I may have found a solution, but I don't understand it. I found it here: [http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

It says to edit:  /etc/modprobe.d/alsa-base.conf and add:

```
options snd-hda-intel model=thinkpad
```I don't know how to do this. Can someone help me?

hit alt+f2 and run the command 

```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

that will open the file in the text editor gedit.

---

### Post by smiley07 on 2011-09-09
> **Ms_Angel_D said:**
> hit alt+f2 and run the command 

```
gksu gedit /etc/modprobe.d/alsa-base.conf
```that will open the file in the text editor gedit.

It worked for my headphones! Thanks!

Now, I've run into another problem, I don't know how to actually turn the microphone on and test it to see if it works. Do you know how to turn on the microphone?

Nevermind I got it to work!

---

