---
title: "Ubuntu 12.10 minimal - How to make analog audio device default ?"
date: 2013-03-22
forum: New to Ubuntu
---

### Post by cwkid on 2013-03-22
Hi

Hoping someone can help me, [I have a problem with one of my TVs]("http://forum.xbmc.org/showthread.php?tid=159654") and for some unknown reason it cannot handle HDMI audio being outputted from the XBMC PC, which is Ubuntu 12.10 minimal / XBMC V12.1

So I'd like to use the green 3.5mm port on the back of the PC and output analog audio to the DVI / Audio in on the back of the TV. 

I have connected the analog cable and changed the audio output device in XBMC system settings to be the Analog device, there are two analog devices listed I have tried both, but I get no sound. 

Been in to Alsamixer and unmuted everything. 

Using an Intel DH67CF itx media motherboard.

Is there anything else I need to do to enable analog audio output ?

Thanks.

[COLOR=#000000][FONT=Verdana]xbmc@xbmc02:~$ aplay -l[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]**** List of PLAYBACK Hardware Devices ****[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Subdevices: 0/1[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]xbmc@xbmc02:~$

[/FONT][/COLOR]```
[COLOR=#000000][FONT=monospace]xbmc@xbmc02:~$ aplay -L[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]null[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Discard all samples (playback) or generate zero samples (capture)[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]sysdefault:CARD=PCH[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, ALC892 Analog[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Default Audio Device[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]front:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, ALC892 Analog[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Front speakers[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]surround40:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, ALC892 Analog[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    4.0 Surround output to Front and Rear speakers[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]surround41:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, ALC892 Analog[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    4.1 Surround output to Front, Rear and Subwoofer speakers[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]surround50:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, ALC892 Analog[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    5.0 Surround output to Front, Center and Rear speakers[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]surround51:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, ALC892 Analog[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    5.1 Surround output to Front, Center, Rear and Subwoofer speakers[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]surround71:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, ALC892 Analog[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]iec958:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, ALC892 Digital[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    IEC958 (S/PDIF) Digital Audio Output[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]hdmi:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, HDMI 0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDMI Audio Output[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]hdmi:CARD=PCH,DEV=1[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, HDMI 1[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDMI Audio Output[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]dmix:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, ALC892 Analog[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Direct sample mixing device[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]dmix:CARD=PCH,DEV=1[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, ALC892 Digital[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Direct sample mixing device[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]dmix:CARD=PCH,DEV=3[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, HDMI 0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Direct sample mixing device[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]dmix:CARD=PCH,DEV=7[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, HDMI 1[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Direct sample mixing device[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]dsnoop:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, ALC892 Analog[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Direct sample snooping device[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]dsnoop:CARD=PCH,DEV=1[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, ALC892 Digital[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Direct sample snooping device[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]dsnoop:CARD=PCH,DEV=3[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, HDMI 0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Direct sample snooping device[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]dsnoop:CARD=PCH,DEV=7[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, HDMI 1[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Direct sample snooping device[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]hw:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, ALC892 Analog[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Direct hardware device without any conversions[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]hw:CARD=PCH,DEV=1[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, ALC892 Digital[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Direct hardware device without any conversions[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]hw:CARD=PCH,DEV=3[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, HDMI 0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Direct hardware device without any conversions[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]hw:CARD=PCH,DEV=7[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, HDMI 1[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Direct hardware device without any conversions[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]plughw:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, ALC892 Analog[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Hardware device with all software conversions[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]plughw:CARD=PCH,DEV=1[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, ALC892 Digital[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Hardware device with all software conversions[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]plughw:CARD=PCH,DEV=3[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, HDMI 0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Hardware device with all software conversions[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]plughw:CARD=PCH,DEV=7[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    HDA Intel PCH, HDMI 1[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Hardware device with all software conversions[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]xbmc@xbmc02:~$[/FONT][/COLOR]
```[COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]

---

### Post by cwkid on 2013-03-22
This is interesting, If I bootup the XBMC PC and once on the XBMC main menu, I then unplug the HDMI cable leaving just the analog 3.5 mm audio cable connected from back of PC to TV, if I then select either analog audio output device from the XBMC Audio Settings:


HDA INTEL PCH, ALC0892 ANALOG 
DEFAULT (HDA INTEL PCH, ALC0892 ANALOG) 


then it works, I can hear through the TV speakers the music track I am playing in XBMC via analog audio out !


However when I plug the HDMI cable back in to the PC the music can no longer be heard, so the HDMI connection is taking priority over Analog audio.


For this particular setup I need Video via HDMI and Audio via analog 3.5mm out. 


[IMG]https://qvtiua.dm1.livefilestore.com/y1p5SCr98neu538EPrfsGGD4JcmwclVGO6aM-YvAU76WBbosFuojamdnhjPvAWMD7TRMivU8yDm7dA/Alsamixer-no-analog.jpg?psid=1[/IMG]

[COLOR=#000000][FONT=Verdana]Seems I need to be using Device 0

card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]

If I use this command in Terminal (Whilst HDMI cable unplugged) I can hear the test sound on the TV speakers

speaker-test -D plughw:0,0 -c 2

So I guess I just need a way to make Audio Device 0 the default device and so it does not use the HDMI device for audio. If I knew how to do that, that is.[/FONT][/COLOR]


[RIGHT][COLOR=#000000][FONT=Verdana][/FONT][/COLOR][/RIGHT]

---

### Post by AlecJ on 2013-03-22
sounds more like the TV is shutting down the audio in when you plug in the HDMI?
anything in the menus on the TV?

---

### Post by cwkid on 2013-03-22
> **AlecJ said:**
> sounds more like the TV is shutting down the audio in when you plug in the HDMI?
anything in the menus on the TV?

Not that I can see no, nothing really related in the TV menus regarding the HDMI3 port on the TV which is for DVI and next to that is a 3.5mm port for the audio in. 

I think I need to make the analog audio device on the PC the default device rather than the HDMI audio, but don't know how to do this. 

Thanks

---

### Post by AlecJ on 2013-03-22
I knew I'd read this before somewhere
[http://ubuntuforums.org/archive/index.php/t-1370383.html](http://ubuntuforums.org/archive/index.php/t-1370383.html)

more info here
[http://www.alsa-project.org/main/index.php/SoundcardTesting](http://www.alsa-project.org/main/index.php/SoundcardTesting)
[http://askubuntu.com/questions/14077/how-can-i-change-the-default-audio-device-from-command-line](http://askubuntu.com/questions/14077/how-can-i-change-the-default-audio-device-from-command-line)

I have had in the past where a current flows from the outer of the HDMI plug (screen) and causes strange things to happen, worth a test to rule it out.

---

### Post by cwkid on 2013-03-22
This is Ubuntu 12.10 minimal I don't think Pulse Audio is installed just Alsa.

If I run these commands whilst the HDMI cable is not connected

[COLOR=#000000][FONT=Verdana]speaker-test -D plughw:0,0 -c 2[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]aplay -D plughw:0,0 /usr/share/sounds/alsa/Front_Center.wav

[/FONT][/COLOR]Then I get sound out of the analog 3.5mm port on the PC to the TVs inbuilt speakers. But when the HDMI cable is connected the analog audio no longer works. 

Thanks

---

### Post by cwkid on 2013-03-22
I think the problem is with my Samsung TV set [COLOR=#000000][FONT=Verdana] LE37R88BDX-XEU[/FONT][/COLOR]

[http://forum.xbmc.org/showthread.php?tid=160102&pid=1374736#pid1374736](http://forum.xbmc.org/showthread.php?tid=160102&pid=1374736#pid1374736)

---

### Post by AlecJ on 2013-03-22
may well be, is there a firmware update on there web site for the TV?

---

