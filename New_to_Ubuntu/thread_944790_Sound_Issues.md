---
title: "Sound Issues"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by kristeee on 2008-10-11
Hello.  After messing with windows for all of my life, I figured giving a linux OS a chance would be fun.  But man, I am overwhelmed.

First things first, I want to basically accomplish everything I can using windows.  The only things I use windows for are ET:RTCW, Ventrilo, XFIRE, and SETPOINT.  

So, after experiencing a couple of sweet things about Debian, I decided to try UBuntu since it is compatible with HIDPOINT, that I thought was like SETPOINT.  Well, I was wrong.  HIDPOINT doesn't allow you to bind your extra mouse buttons to your keyboard.  (I only wanted my mouse buttons bound to numbers 1-6. With the Logitech mx600 mouse.) 

After that disappointing discovery, I decided to stick with ubuntu, for I want to learn.  I have researched different methods of binding buttons on your mouse to your keyboard and have been unsuccessful.  If I could get any help here, that would be great.

Now, at the same time, I want ventrilo to work via wine.  I have ventrilo working, but if the ventrilo window isnt the active window, I cannot hold down my push to talk button.  I have come across many suggestions to this problem, but again, have been unsuccessful.  If I could get any help I would very much appreciate it.  Also, ventrilo recognizes no sound mixer.  It did when I first installed it, but after I figured out that the ET sound didn't work while I was connected to ventrilo, I messed around with some sound settings. 

Now, at first, the sound in game worked fine, as long as I ran ET before I ran another program which needed to use sound.  Basically, I can only run 1 program at a time if the program uses sound.  For example, if I run ventrilo 1st, I can hear sound, but if I run ET after ventrilo, the sound in ET will not work.  This whole sound issue, is a pain in my ***.  I believe I have royally screwed up the sound for ET by modifying the sound options so both ventrilo and ET would work together.  With that all being said, there are two issues at hand here. 1- Sound in multiple programs at once 2-  Faking ventrilo so I can use Push to talk.  I have read many forums and tried many suggestions, but again, I am a noob at this all.

I get this in the terminal when I try to run ET:
[NOTE: I am using ETH-X] (If that even matters.) 
(My brother also installed et-sdl-sound, which he told me allows ET to have sound as well as other programs all at the same time.)



------- sound initialization -------
SDL audio driver initializing...
SDL audio driver is "alsa"
SDL audio initialized.
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
16384 samples
   16 samplebits
    1 submission_chunk
44100 speed
0x0x9c096b80 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/kristeee/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/kristeee/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/kristeee/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/root/enemy-territory//etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xb7d5d970  
Sys_LoadDll(ui) succeeded!

FIrst off, how do I unmute system sound?

I have my sound playback and sound capture as ALSA.

I have also tried to move or copy ui.mp.i386.so into /home/kristeee/.etwolf/etmain/
That was unsuccessful as well. 

If anyone out there would be so kind as to help a lady out, I would much appreciate it. 

By the way, I am using an HP a1323w computer with an ATI Radeon 2600 series graphics card.  This card also comes with an HDMI hook up that includes sound as well.  I do not use it, I use the onboard sound.  So maybe there is an issue there?  I have no idea.

Thanks,
Kristeee

---

### Post by markbuntu on 2008-10-11
Welcome to Unbuntu.

You just need some setup help. Go here, start at the Multiple Application Sound Sharing section or, if you have not messed around in you sound configuration files and broken anything, the Packages section. This will get your sound dialed in. Don't forget to look in any interesting links:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

If you want an explanation of how it works:

[http://ubuntuforums.org/showthread.php?p=5931543](http://ubuntuforums.org/showthread.php?p=5931543)

---

### Post by kristeee on 2008-10-12
:confused:

It's not that I can't comprehend what I read, trust me that is no issue.  I just have no experience with any of this.  FFS, I came from windows, I am a lazy *******.  I think everything is just suppose to work.  I cannot get sound back in ET.  When I run it through terminal now, I get:

------- sound initialization -------
SDL audio driver initializing...
SDL_AudioDriverName() = NULL
------------------------------------
Sound memory manager started
Sys_LoadDll(/root/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/root/.etwolf/etmain/ui.mp.i386.so) failed:
"/root/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/root/enemy-territory//etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xb7d2c970  
Sys_LoadDll(ui) succeeded!


Please help.  If I could just get sound working in ET again, I would be happy.

---

