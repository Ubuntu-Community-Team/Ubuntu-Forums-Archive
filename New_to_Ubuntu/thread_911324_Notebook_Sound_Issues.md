---
title: "Notebook Sound Issues"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by AutomaticJack on 2008-09-05
While unpacking from my latest move I came across my old laptop (Gateway 4024GZ). It bit the dust well over a year ago... so I decided to wipe the hard drive and install Ubuntu 7.04. I'm still checking it out and will probably run it through its paces this weekend, but the first thing I noticed was NO SOUND! I'd appreciate any help or suggestions... shamefully, I'm a total newb!

---

### Post by jbrown96 on 2008-09-05
check if your hardware is supported by alsa. Your best bet is to find a thread that has delt with this hardware before. It might be better to upgrade to a more current distro as hardware support is always getting better. 

0. (thought about this afterwards) go into the sound preferences (either preferences or administration) and mess with the playback device. Just get some audio playing and mess with it.
0.5 try ```
alsamixer
``` use the arrow keys to switch between channels, up/down to adjust volume, m to (un)mute channels. Maybe the channel is muted. I would advise you to mute all unnecessary channels because there may be problems with feedback.
1. find your hardware. In a terminal (apps-->accessories-->terminal) ```
lspci | grep Audio
``` If that doesn't return anything, try ```
lspci
``` and sift through the output until you find the audio line.
2. use the google to see if someone else has the same problem with your hardware
3. post back if you can't find a solution, or post back with the solution that works so others can find help easier.

sorry about the numbering...

---

### Post by AutomaticJack on 2008-09-07
ok...I upgraded to 8.04 and played with the mixer. Then I followed your numbered suggestions and here's what I came up with: 

lspci | grep Audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

Nope... still no sound. I even tried plugging in earphones (the speaker could have been shot... right?)


As I said.... I'm a total newb with this (too much microsoft poisoning I shouldn't wonder... and a few years beyond my true tech prime)!

---

### Post by jbrown96 on 2008-09-07
I search for problems with your hardware and couldn't find much. There was a problem with kernel 2.6.24-12 (which may be the original for hardy), so that may be causing the problem. I read a couple of posts that pointed back to alsamixer. One of them used a program called gnome-alsamixer, which may be easier for you to use since you are new. You can find it in synaptic or ```
sudo apt-get install gnome-alsamixer
```
run all updates if you already haven't, and if prompted, restart.
then check your kernel version with ```
uname -a
``` It should give you something like this > 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux. I'm not using the newest kernel; I believe it is 2.6.24-21 or -20. It doesn't matter as long as it is after -12. 
If you try to play audio, is there an error or just no sound?

---

### Post by AutomaticJack on 2008-09-07
No sound at all! An error would be something...

I mean, I can live with it. I really only resurrected this laptop to have a platform with which to familiarize myself with linux to begin with. I'm just used to being able to troubleshoot and make things WORK!

---

### Post by jbrown96 on 2008-09-09
If you're not getting an error then I wouldn't think it is a problem with the sound system. It is more likely related to muted playback. Check all sound applications and make sure they are not muted. Did you try gnome-alsamixer? You also may want to change the playback device in your sound preferences.

---

