---
title: "Few problems with Ubuntu 13.04 (sound, graphic, installations)"
date: 2013-08-12
forum: New to Ubuntu
---

### Post by gstoyanov on 2013-08-12
[COLOR=#333333][FONT=UbuntuRegular]Hi,

I'm new and I have few problems with ubuntu. 
1) First is that i have spikes while played any sounds (mp3,youtube etc..) above 40-50%. I searched the web and try thisone,but I still don't know what is wrong: ```
sudo aplay -l
``` and there is what terminal prints:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]```
**** List of PLAYBACK Hardware Devices **** card 0: SB [HDA ATI SB], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog] Subdevices: 0/1 Subdevice #0: subdevice #0 card 0: SB [HDA ATI SB], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital] Subdevices: 1/1 Subdevice #0: subdevice #0
```
2) I can't explain well other problem so I'll show you:
 [IMG]http://i.stack.imgur.com/hpJDi.png[/IMG] [/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]This is only when i go to dash, or alt+tab, I mean that my desktop doesn't looks like that, but it's still annoying :/[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]3) When I want to install gnome or Synaptic and Compiz ( maybe and other apps ) terminal print:[/FONT]
```
[COLOR=#222222][FONT=Verdana]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)[/FONT][/COLOR]
```[/COLOR]```

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

3) FIXED: Just restart the PC xD

[COLOR=#333333][FONT=UbuntuRegular]Can someone help me with this issues, please ? :)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]ps sorry for bad English
ps2 my machine is 32-bit.
ps3 when I installed ubuntu, I let it to upgrade all things he wanted :)[/FONT][/COLOR]

---

### Post by GwL3eNC on 2013-08-12
Hi, it's about number 3.

If you want to install an application you must do that as sudo.
Type

sudo apt-get install gnome

and it works!

---

### Post by gstoyanov on 2013-08-12
First, 10x for advice, but when I tape sudo apt-get install gnome shows that I posted on thread.

I have another one problem .... when i move volume control slide on youtube to max automatically ubuntu mute the volume :X 
I'll need some help about this things, it's very hard to do anything while u have problems like this. :(

---

### Post by Vladlenin5000 on 2013-08-13
1) What do you mean by "spikes", exactly? You may need to select the correct sound device output? Which devices are listed in sound preferences?

2) Graphics drivers issue. What's your graphics card?

3) Some other process is currently installing something, usually updates.

---

### Post by gstoyanov on 2013-08-13
1)I mean for less than a second stops music and then continue. When sound spikes  in sound application I saw that for less than a second (in same time!) shows other thing in "Play sound through" and I think that's headphone... but i didn't have any headphone connected to PC :( 
[http://prikachi.com/images/794/6441794q.png](http://prikachi.com/images/794/6441794q.png) 
PS Digital output dosen't work! (Or it's muted i don't know, when i select it music stops)

2) Advanced Micro Devices [AMD] nee ATI RS690 [Radeon X1200]

3) At the moment things are ok :)

---

### Post by Vladlenin5000 on 2013-08-13
1) Sorry, can't help you further with that one. It looks like a hardware issue.

2) AMD/ATI has been a huge headache since... Ever. You should try proprietary drivers One of those available at software & updates --> Additional drivers should work fine. Note: I'm not entirely sure about the spelling. My system is in Portuguese right now.

3):D

---

### Post by 3rdalbum on 2013-08-14
1. Run "alsamixer" and turn the PCM audio channel down to 80% or thereabouts. Your sound should now be less distorted at high volume.

2. The ATI x1200 graphics card is not supported by ATI anymore and as a result it wont work very well on Linux. The open-source driver which you are using is the only driver available. You might be able to turn off transparency and animations in Unity to work around the display problem- have a look on Google for a guide. Otherwise, buy a recent Nvidia graphics card.

---

### Post by 3rdalbum on 2013-08-14
> **Vladlenin5000 said:**
> You should try proprietary drivers One of those available at software & updates --> Additional drivers should work fine.

No, there are no additional drivers for the X1200, ATI/AMD dropped support three years ago.

---

