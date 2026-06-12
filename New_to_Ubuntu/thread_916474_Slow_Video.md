---
title: "Slow Video"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by RussW210 on 2008-09-10
I can't seem to get movies running at a normal speed.  Seems like they are running at a rate of 1-2 frames per second.

I use VLC Player and have a few .avi movies that ran with no problem.  However, I have some home videos off my digital camera that run VERY slow on the Totem Movie Player, and don't run at all off the VLC Player.

When I go online to click a video clip (something that would normally run fine with QuickTime on Windows) the clip is EXTREMELY slow.  Yet, YouTube videos run fine.

I don't even know where to start with this.  Is there something I need to download in Synaptic Package Manager?  PLEASE HELP!!!

---

### Post by RussW210 on 2008-09-10
With the home video's (which are also .AVI) I get the error message "Unable to open 'file:///media/250GB%20HDD/MUSIC,%20PICS,%20VIDEOS%20250/PICTURES+VIDEOS%20250/Family/MVI_0011.AVI'" on VLC Player.  They just run at the 1-2 FPS on Totem.

---

### Post by Crafty Kisses on 2008-09-10
What are your system specs?

---

### Post by RussW210 on 2008-09-10
System Specs:

Dell Inspiron 530
Q6600 Quad-Core Processor
ATI 2400 HD 128MB Video Card
3 GB RAM

Brand new computer.

---

### Post by RussW210 on 2008-09-10
Odd... when I play the movie through my external hard drive (where my home videos are stored) it is slow and choppy.  But if I drag the movie onto my desktop and play it from there using VLC there is no delay or sound issue whatsoever...

Still doesn't explain why it is slow through the external hard drive or even playing videos through websites.

---

### Post by RussW210 on 2008-09-11
But playing the large videos that I have saved on my computer straight through the hard drive presents no problem.

I am thinking this is a problem tailored toward specific video files... or maybe I am missing some codecs or plugins... because like I said my camera's videos are AVI.

---

### Post by linux5uper on 2008-09-11
Don't know if the nature of your problem is the same as mine, but I followed the instructions here

[http://ubuntuforums.org/showthread.php?t=789578&highlight=audio+fix](http://ubuntuforums.org/showthread.php?t=789578&highlight=audio+fix)

and the audio system fixes fixed my slow-playing videos (only played slowly in totem). It's basically got to do with the bad implementation of pulse audio in the current version (8.04). 

I guess it's not a bad idea to apply these fixes anyway.

---

### Post by RussW210 on 2008-09-11
I will try those instructions and report back, linux... I had issues with Pulse Audio when I first installed Ubuntu.  Maybe I disabled something.

---

### Post by RussW210 on 2008-09-11
OK... I have libsdl1.2debian-alsa installed in my computer right now.  I did this because I was having problems getting sound on an emulator I was using... however your website suggests trying the pulseaudio... which automatically deletes the alsa pacakage...

Could this have something to do with it?

---

### Post by Crafty Kisses on 2008-09-11
Post the results of this command:
```
top
```
It could be a resource issue.

---

### Post by RussW210 on 2008-09-11
top - 07:37:42 up 3 min,  2 users,  load average: 0.41, 0.36, 0.15
Tasks: 142 total,   2 running, 140 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.6%us,  0.3%sy,  0.0%ni, 99.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3114564k total,   689240k used,  2425324k free,    14920k buffers
Swap:  6000268k total,        0k used,  6000268k free,   274792k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5803 root      20   0  313m  77m  19m S    1  2.5   0:04.54 Xorg               
 6426 russell   20   0  149m  55m  19m S    1  1.8   0:03.04 firefox            
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.30 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/2        
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3        
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/3        
   14 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/3         
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0          

I am not sure why it says "2 users" when I am the only user.

---

