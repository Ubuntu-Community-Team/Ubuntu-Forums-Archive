---
title: "Cloud with Wine"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by DonaldTrumpsAlterEgo on 2008-08-07
Hello all,

I am trying to run the game cloud using Wine.  Firstly I am having trouble configuring Wine, I had it working at one point, but it stopped when I added  flash to firefox.  In winecfg I couldn't configure any of the audio drivers as the audio test always failed.  I purged wine from my computer and reinstalled it, the audio problem still existed and so did all the program files, which makes me think it wasn't completely removed.  I used the command line ```
sudo apt-get purge wine
```.  

I then installed cloud, thinking who needs sound anyway.  It installed fine, but when I navigated to the c drive and the folder with the .exe and ran wine cloud.exe I got
 ```
playtime@master-desktop:~/.wine/drive_c/Program Files/Cloud/bin$ wine cloud.exe
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
wine: Unhandled page fault on read access to 0x68732f6c at address 0x7e05b752 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x68732f6c in 32-bit code (0x7e05b752).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e05b752 ESP:0033faec EBP:0033fb14 EFLAGS:00010206(   - 00      - RIP1)
 EAX:68732f6c EBX:7e07aea8 ECX:001242d8 EDX:001242f8
 ESI:006d0a68 EDI:68732f6c
Stack dump:
0x0033faec:  00000000 0033fb10 7e13db8c 00000000
0x0033fafc:  00000000 00000001 00000000 00000000
0x0033fb0c:  006d0a68 7e12dc50 0033fc28 0040436e
0x0033fb1c:  68732f6c 86000000 006d0a68 00000000
0x0033fb2c:  00404db3 00000300 006d0a68 00000001
0x0033fb3c:  00040000 00000000 00000000 00000400
Backtrace:
=>1 0x7e05b752 wglDeleteContext+0x32(hglrc=0x68732f6c) [/build/buildd/wine-0.9.46/dlls/gdi32/opengl.c:97] in gdi32 (0x0033fb14)
  2 0x0040436e in cloud (+0x436e) (0x0033fc28)

```

which being a newbie i had no clue how to interpret.  i am running xubuntu gutsy on an old gateway with only 256 mb of ram.  Offhand I have no clue what the sound card is I could find out if the need exists.  Also if someone could direct me to somewhere where I could learn how to understand the above code and future ones that would be cool.  Or even just deciphering snippets, if not that is chill too.  Well thank you in advance.

---

