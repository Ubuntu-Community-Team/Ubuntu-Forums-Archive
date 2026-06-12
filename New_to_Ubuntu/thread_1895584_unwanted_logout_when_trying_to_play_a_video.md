---
title: "unwanted logout when trying to play a video"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by noob5000 on 2011-12-15
i have freshly installed ubuntu studio 11.04 "natty" on an old desktop pc (1.8 mhz  monocore) and everything is fine, except:

when i try to play a video file with movie player or vlc, it works only for a moment. 
then suddenly the screen turns black (and the audio signal stops simultaneously). 
after some seconds of black silence comes the login-screen and all data from the session before is lost.

i  have searched this forum for a while and i think the spontaneous  logouts indicate the X server crashing. 
i have no idea why exactly the X server would crash, but clearly it is somehow triggered  by attempts to play videos. how can this be?

---

### Post by whitethorn on 2011-12-15
What kind of graphic card do you have and what drivers do you have installed? 

Start Vlc go to Tools -> Preferences -> Video and try changing it from default to X11 or GLX and see if you can then play a video.

---

### Post by noob5000 on 2011-12-15
thanks for your reply! :)

the pc has no extra graphic card, only the standard onboard vga output on the rear, next to the ps2 ones.
system/preferences/monitors detects an "unknown monitor", no specific drivers (nvidia etc) are mentioned there. 

changing the vlc output to X11 has worked, it plays videos now without logout-syndromes.
but the default player (totem player) has no such output options, so it still causes the sudden logouts. 

so it has something to do with the default video output channel to the x server?


also, i have installed ubuntu 10.04 LTS on the free partition, just to see if there are any problems with another system. and sure enough: 10.04 crashes instantly with the session start. after the installation & restart i could only login once. i changed the desktop background and rebooted. since then i cannot even login... the login leads directly into blackness and then back to the login screen. maybe this is also the x server crashing? 
i never encountered this logout crash problem on a pc (with 2 different versions of ubuntu!). btw on the same pc i had ubuntu 9.04 running successfully and without problems, for 2 years. but 9.04 is not supported anymore so i need a newer ubuntu. this logout problem must be solved somehow???

---

### Post by noob5000 on 2011-12-15
btw same situation with dvd: 

vlc (with video output changed from default to x11) works, default totem player instantly crashes the session.

i cannot just ignore the problem and only use vlc because every now and then the default player will be needed, and every time i will lose all data open in the session. the login sessions must be stable, anything else is a reason to install windows (the horror!) if it is more stable than ubuntu... i am not yet prepared to accept that.

---

### Post by Mark Phelps on 2011-12-15
The PC must have a graphics chip (unless integrated with the CPU), otherwise, you would not get video ...

So, please open a terminal, enter "lspci" -- and look for the line containing "VGA".  That will tell us what make and model graphics chip your PC is using.  Please post that line back here.

---

### Post by noob5000 on 2011-12-15
ok this is what lspci brings up (VGA is in the last line):

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8623 [Apollo CLE266]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:07.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 81)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics (rev 03)

```

---

### Post by gandaran on 2011-12-15
> changing the vlc output to X11 has worked, it plays videos now without logout-syndromes.
but the default player (totem player) has no such output options, so it still causes the sudden logouts. 
totem does have it too!
type in terminal
```
gstreamer-properties
```

---

