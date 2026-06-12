---
title: "no sound!"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by klqd on 2012-07-21
i only have headphones no speakers. these are plugged in. the volume setting top right is "on", as are the first four settings on alsamixer - master headphone pcm and front.


thanks :popcorn:

Card: HDA NVidia                                     
Chip: VIA VT1705
worked before installing 12.04

---

### Post by NikTh on 2012-07-21
Hi , 
open sound settings and check out if headphones are primary (selected) device for output.

Regards

---

### Post by klqd on 2012-07-21
headphones are top of the two item list of "play sound through" and are highlighted.

test sound gives no sound.

---

### Post by jmfal on 2012-07-21
Run this in a terminal:
```
 aplay -l   
```
and
```
 lspci | grep -i audio   
```

And post the results between the [CODE][CODE] brackets using # above.

---

### Post by klqd on 2012-07-21
```
luke@luke-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1705 Analog [VT1705 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 2: VT1705 HP [VT1705 HP]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
```
luke@luke-desktop:~$  lspci | grep -i audio
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
luke@luke-desktop:~$ 

```

---

### Post by jmfal on 2012-07-21
Let's try adding this line to
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf    
```
Enter password
Scroll to end of file
enter this line
```
 options snd-auto enable=yes   
```

Save/close ,, be sure to save to the "etc" file (click save ,, in window ,,click etc, click save
Restart pc/laptop
Check alsamixer (not muted)
Check sound
If there is something similar in file, don't edit

---

### Post by klqd on 2012-07-21
did not work.

there was already ```
options snd-usb-audio index=-2
``` in the file. i wasn't sure what you meant by saving to etc, i just saved as normal. - which makes the file path of the etc file flash up art the bottom of the window.

---

### Post by jmfal on 2012-07-21
thats OK
 What kind of pc/laptop are you using
And are you using a usb sound card

Its easier to figure out  problems if all info...................

---

### Post by klqd on 2012-07-21
no i'm plugging in my headphones to the pc's headphone jack? it worked fine before the upgrade.

i don't know what information you need etc. about my pc. it's a desktop build - not by me  i just chose its relatively cheap components.

---

### Post by jmfal on 2012-07-21
Thats alright 
If you're using on-board sound then open that file  and remove that option and enter the one I gave you
save/close file 
restart 
check mixer
check sound

---

### Post by klqd on 2012-07-21
> **jmfal said:**
> Thats alright 
If you're using on-board sound then open that file  and remove that option and enter the one I gave you
save/close file 
restart 
check mixer
check sound
ok so it's back to how it was at the start. the sound's not working. what now?

---

### Post by jmfal on 2012-07-21
Try changing sound cards in mixer and sound settings
sometimes you have to have to go back and unmute everything and try different combinations
I'm working on it so don't get discouraged.

---

### Post by klqd on 2012-07-21
> **jmfal said:**
> Try changing sound cards in mixer and sound settings
sometimes you have to have to go back and unmute everything and try different 

i don't seem able to find those settings, sorry.

---

### Post by jmfal on 2012-07-22
Click on the alsamixer link below

---

### Post by klqd on 2012-07-22
i pressed f6 and chose usb midi then exited and went back in and selected the sound card again but nothing has changed.

---

### Post by jmfal on 2012-07-22
If you are trying to get sound from midi keyboard you should have said that in your first post.

Open sound settings and select input/capture, select midi, unmute and increase volume/gain

---

### Post by klqd on 2012-07-22
no i'm not trying to!!

i was just trying to follow your instructions - of deselecting and reselecting the sound card.

---

### Post by klqd on 2012-07-22
how do you change soundcards? i see no option for that in alsamixer. pressing f6 gives me the option of changing settings for the sound card or usb midi but i don't see a way of changing soundcards...

sorry for the last misunderstanding.

---

### Post by Hadaka on 2012-07-22
this option should NOT be removed..it is related to a usb port
has nothing to do with audio headphone or speaker.

options snd-usb-audio index=-2

if you removed it i would suggest putting it back

```
 gedit /etc/modprobe.d/alsa-base.conf
options snd-usb-audio index=-2
 
```

---

### Post by jmfal on 2012-07-22
In alsamixer you have to use the arrows  on the keyboard to navigate.

To change sound card press F6 use up/down arrows to select card

When you have selected card press enter
Press the "esc" key to exit window

To adjust the volume controls press F5
again use left/right arrows to select volume 
to unmute press m
to increase volume use up/down arrows on keypad

---

### Post by klqd on 2012-07-22
no that line was still there.
f6 in the mixer only gives me the option of selecting default, the nvidia sound card, or the usb midi.

---

