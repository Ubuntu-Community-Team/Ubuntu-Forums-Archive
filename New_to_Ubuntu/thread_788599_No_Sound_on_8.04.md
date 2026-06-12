---
title: "No Sound on 8.04"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by brandon89 on 2008-05-09
hey, so this is basically my first time working with ubuntu.  i figured that id give it a try since a lot of people have been talking about it.  i installed it and i do like it however, i cant seem to get any sound from my laptops speakers.  i checked and i can get sound when i have my headphones plugged in.  any suggestions?  thanks.

---

### Post by macaholic on 2008-05-09
Check in the sound preferences, System > Preferences > Sound (assumed gnome) to see what device is selected, and see if selecting different ones makes a difference.

---

### Post by Xiong Chiamiov on 2008-05-09
There is also a gigantic guide [here]("http://ubuntuforums.org/showthread.php?t=205449") that will pretty much solve all your problems, if it comes down to it.

---

### Post by brandon89 on 2008-05-09
tried all the devices and nothing changed.  i also checked to make sure nothing was muted in the volume settings.

EDIT: ok ill look into that guide, thanks

---

### Post by brandon89 on 2008-05-09
ok well i tried the guide, but still no sound from the speakers =(

step 1 returns
```
brandon@brandon-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
brandon@brandon-laptop:~$ 

```

so then i go down to the alsamixer steps and nothing is muted....

---

### Post by Xiong Chiamiov on 2008-05-09
What do you get from
```

asoundconf list

```

---

### Post by brandon89 on 2008-05-09
```
brandon@brandon-laptop:~$ asoundconf list
Names of available sound cards:
NVidia
brandon@brandon-laptop:~$ 
brandon@brandon-laptop:~$ 

```

---

### Post by Xiong Chiamiov on 2008-05-09
You can try making sure that that card is set as default:
```

asoundconf set-default-card nvidia

```
That said, it shouldn't be a problem if you can enter alsamixer properly:
```

alsamixer

```
You might need to sudo apt-get install alsamixer.

---

### Post by brandon89 on 2008-05-09
this is kinda weird...

```

brandon@brandon-laptop:~$ sudo apt-get install alsamixer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsamixer
brandon@brandon-laptop:~$ 

```

and when i just try to open alsamixer i get this
```

brandon@brandon-laptop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
brandon@brandon-laptop:~$ 
```

---

### Post by Xiong Chiamiov on 2008-05-09
As for the first one, I probably gave you the wrong package name.  It doesn't matter, however, because you have it installed.

The second error is what the asoundconf set-default-card command is supposed to fix.  Try using the same capitalization as shown when you ran the list command, then reboot.

---

### Post by brandon89 on 2008-05-09
ok well i fixed the set card default thing, but i still have no sound coming from my speakers.  (just to rule this out, in windows i do get sound so they arent faulty).

---

### Post by Xiong Chiamiov on 2008-05-10
Hmm, you might try compiling the alsa drivers from source (it's a bit of a ways down in that guide).  Also, first, launch alsamixer and make sure everything that can be is turned up to a medium-high volume.  You can scroll left and right with the arrow keys, and use up and down to change levels.

---

### Post by brandon89 on 2008-05-10
SWEET!! the recompiling thing worked! thanks so much

---

