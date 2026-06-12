---
title: "MP3's not playing -- but they should"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by ElseIf on 2008-04-29
I've installed ubuntu-restricted-extras, and searched up a lot, but I can't find out why. I don't get any error messages or anything, but the slider just won't start moving, and the song won't play. 

Any help would be appreciated.

---

### Post by waawaawee on 2008-04-29
try installing xmms 

goto system>adminstration>synaptic package manager
search for xmms and then install it or 
or type on terminal
sudo apt-get install xmms

this should fix the problem

---

### Post by stchman on 2008-04-29
> **ElseIf said:**
> I've installed ubuntu-restricted-extras, and searched up a lot, but I can't find out why. I don't get any error messages or anything, but the slider just won't start moving, and the song won't play. 

Any help would be appreciated.

Here is the CODECs to install to get MP3s to play.

```

sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

Make sure you have all the repos enabled.

---

### Post by ElseIf on 2008-04-29
Thanks for the replies, but I have both of those installed already.

---

### Post by FreewheelinFrank on 2008-04-29
w32codecs?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by ElseIf on 2008-04-29
Nope, I've installed those also. =/

---

### Post by unutbu on 2008-04-29
Did you check /var/log/messages (for warnings/errors related to audio)?

Also post

```
aplay -l
cat /proc/asound/cards
lspci | grep -i audio
sudo lshw -C multimedia

```

---

### Post by ubuntu-freak on 2008-04-29
Odd problem you have there. Do videos and Flash streams play okay? Which applications have you tried to play your mp3's? Have you installed any Xine packages? Give part 1 of my how-to a try in my sig, just incase.
 
Nathan

---

### Post by ElseIf on 2008-04-29
Oh, the sound works. It's merely for MP3's that it doesn't.

EDIT: Scratch that, it doesn't work for videos or audio that I've downloaded, but flash and streams work perfectly. I'm really confused now.

Output of the command:

```
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
owner@owner-desktop:~$ cat /proc/asound/cards
 0 [CA0106         ]: CA0106 - CA0106
                      Audigy SE [SB0570] at 0x1100 irq 20
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0x90200000 irq 18
owner@owner-desktop:~$ lspci | grep -i audio
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
02:04.0 Multimedia audio controller: Creative Labs SB Audigy LS

```

And no, I didn't check that file. I didn't even know you could do that.

I have installed xine packages, yes. I'm not sure what they were now. =/

---

### Post by ElseIf on 2008-04-29
Hey, really really sorry about this everyone. I restarted (I'd done this already, but it didn't work) and it worked fine after that. Weird, but at least it worked. Thank you!

---

### Post by ubuntu-freak on 2008-04-29
Haha. That's why my how-to says to reboot in about three sections.
 
Glad you got it working.
 
Nathan

---

