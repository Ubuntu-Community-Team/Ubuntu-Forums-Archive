---
title: "how can i setup my sound properly"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by pcool on 2012-02-06
hello ubuntu peoples >i  am french so sorry for bad english... ! i just installed unbuntu studio on my laptop and on my desktop (ver.11.04) .  i started in ubuntu 8.04 and went back and forth from windows to ubuntu four times . I now feel more more confident about having a stable system  i am also giving puredyne a chance  but i don't know if it will last because puredata seams to have library-external issues that i am too newbe to understand so maybe later... but the problem is with _sounds _.... (it's the main reason i alsways go back to windows ... ) i already read a lots of post on forums but there is a few details that i just don't get 

- pulse audio .... is this a driver or a mixer ?
-alsa is the main (driver ?) that pulse audio comunicate with ???
-jack ... very handy with midi devices  but it does not seam to be able to output all programs... can it be used instead of alsa, oss, pulse audio with all programs?
- i can't figure out how to setup wich sound driver to use
- do i need alsa, jack and pulse audio to be installed ?.. i think i'd prefer just one if it is all the same thing
- i have zynaddsubfx installed ... on both (desktop and laptop) ... on my desktop i fiddled with the output location of my dsp (setings) , installed falsh plugin extra-sound and some sort of sound library ... everything is working but my sound is ultimatly destroyed and it sounds worst if i let it play for a while (a metalic sound is uncommonly comming out of the speakers ??? could it be two sound drivers running at the same time? 
-and how can i find the location of my sound card in oss or else ...dev dsp0 ... etc
- is there like an ultimate sound setup that will just work with all programs?

thecnicaly i just want something that works since i am a multimedia artist and don't want to go back to windows for democratics reasons

anyway i  am really confused (more I read posts the more i get  confused seams like there is many ways to configure sound ) so any clue could help me , love you all .... and keep up the good work

---

### Post by Sigma1 on 2012-02-06
From the little I know, "alsa" is the legacy sound manager, while "pulseaudio" is a newer sound manager which is supposed to offer more options and better functions. On different installations I've had pulseaudio work out of the box, or nearly, and I've also had problems, which have ended in me uninstalling pulseaudio and using alsa for everything. From my limited experience, then, it looks to me as if alsa is the safest bet, though the advanced interface (reached via the terminal and alsamixer) is not as user-friendly as pulseaudio's interface.
I don't know much about "jack"!
Hope this helps a little.

---

### Post by pcool on 2012-02-11
hum that make sense ... jack is the basically the same thing as i can understand ... because it shuts pulse audio as soons has it opens .... yesterday i played in kernel setting mode but i couln't figure out how to set the default sound card in grub (with KMS)  or ...IDEALY.. i'd set it up so that alsa becomes my default driver but outputs it in jack if jack is lauched... arrrgh i want that knowledge !!!

---

### Post by Sigma1 on 2012-02-11
Not sure if this will help, but here are two ways of getting rid of pulse, and using alsa in general:

1. on 11.04, remove pulseaudio from the startup applications list (if you use gnome, or ubuntu classic, then you get there via "system", I don't know how to get there with unity), but you can also chose an ubuntu-classic session on login;
2. on 11.10 (at least): Turn PulseAudio autospawn off, normally. ```
echo "autospawn = no" > ~/.pulse/client.conf
``` 
then
```
killall pulseaudio
```
I found the second solution here: [http://community.skype.com/t5/Linux/Solution-for-not-working-microphone-under-Ubuntu-11-10/td-p/298266](http://community.skype.com/t5/Linux/Solution-for-not-working-microphone-under-Ubuntu-11-10/td-p/298266) and ultimately, here: [https://wiki.archlinux.org/index.php/Skype#Skype_can_only_see_pulseaudio.2C_but_not_ALSA_devices](https://wiki.archlinux.org/index.php/Skype#Skype_can_only_see_pulseaudio.2C_but_not_ALSA_devices)
Good luck.

---

### Post by pcool on 2012-02-13
great thanks for the link ! I fixed my flash player sound by removing shockwave plugins adobe-extrasound and installed VLC (perhaps i had too many plugins ...  wich created disturbance in the speakers ... not shure but it's fixed) 

Now I am trying to get jack control output in alsa ... Is this a crazy idea ?

---

### Post by pcool on 2012-02-13
oh yeah and i didnot remove adobe flash plugin

---

### Post by ohnonot on 2012-02-14
...i have basically the same question/idea as pctool.
trying to set up sound editing software it seems they all want jack.
from what i understand about how jack works, that seems logical.

but do i need pulse audio???
my laptop is rather old and crappy (amilo) so i have to save all the ram/cpu i can.

> **pcool said:**
> Now I am trying to get jack control output in alsa ... Is this a crazy idea ?

pctool, did you try to disable pulseaudio following sigma1's advice?
i will try it now and report back later.

is it advisable to just uninstall pulse audio completely???

---

### Post by pcool on 2012-02-14
well what i understood i just ... unable a section of it ... there is still a few details missing ... uninstaling pulse audio won't work(depends on wich version of linux you have ..  i guess) ... i use alsa instead ... but i didn't had the time  to play with jack in combination yet ... so I can't help for now ... but i know you can get alsa-jack or (jack alsa)  package ... i wander what it does but if you know a link where i can get easy jack tutorial ... i'd love it 

... rock-on !!!

---

### Post by ohnonot on 2012-03-01
installed jack, qjackctl and others. takes a while to set up, tricky.
but it works.
uninstalled pulseaudio, most apps work fine, for some there's workarounds.

edit: i'm using xubuntu 11.10

edit (a week later): jack works but feels like a house of card about to collapse all the time. some apps don't support jack, some mysteriously take 70% cpu when running with jack, some have to be connected by hand... youtube has no sound (and flash support for jack doesn't seem to be developed yet)... oh my god...  i just removed jack from auto-startup and am using alsa again. after 2 reboots (sic!) everything is back to normal, meaning: working.

seems working with jack is good for sound creators, but not a solution for the normal user?

---

### Post by Splooshie123 on 2012-03-23
I made a thread about making PulseAudio and Jack work together.

[http://ubuntuforums.org/showthread.php?p=11777073](http://ubuntuforums.org/showthread.php?p=11777073)

EDIT: Oh, you already removed PulseAudio. That works, too. But it means you'll have to fix some applications to use Jack instead of the now nonexistent PulseAudio.

---

