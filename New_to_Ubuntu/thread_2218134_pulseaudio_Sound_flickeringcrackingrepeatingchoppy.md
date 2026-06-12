---
title: "pulseaudio Sound flickering/cracking/repeating/choppy crash youtube amarok vlc flash"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by kalakohad on 2014-04-19
Sorry for a weird title, but i try to made it sure that google will link that thread on many keywords.

So i installed kubuntu and every program what has some sound will flicker on random spots and eventually after a while it crashes the program.
On youtube( so both firefox and chromium) it usually plays a clip around 3-6 seconds as normal, then it freezes and you hear a repeating ~0.3  sound on that part of the clip on several seconds, i call it flickering.  Usually it resumes 2-5 times until in the end it crashes the flash part of youtube. Basicly, the amount of flash and sounds on internet makes web surfing a crashfest. 

On amarok, i can hear internet radio around 1-2 minutes without any problem. Then gradually above mentioned flickering coming in, sometimes faster, sometimes slower but in the end amarok stops playing after ~0.3 sec sound flickering lasts 5-8 seconds. If you immidiately try again to play, you get flickering, but if you wait you get 1-2 min flickering free time.

On  VLC or Dragon player, youmight watch couple of seconds up to 10 minutes until you get the flickering and on end it crashes both.

On system sounds, because on random apperance of flickering and you need it to last several seconds,  its harder to reproduce, but you will get time to time flickering very rarely(when there is multiple notice sounds) a crash to random program too. 

On notice, same thing happened over year ago on debian, ubuntu and kubuntu (on both x86 and x86_64 variants)  when i last time used linux on this laptop. 

So what ive tried.
first Playing a mp3 on alsaplayer is flawless though. So i think think its something with pulseaudio. 

sudo apt-get purge pulseaudio
sudo apt-get install pulseaudio

No change

rm -rf .config/pulse/

no change

edited 
/etc/pulse/default.pa

changed lines

load-module module-alsa-sink device=default tsched=0
load-module module-alsa-source device=hw:0,0 tsched=0
load-module module-udev-detect tshced=0

no change.

some relevant information from alsainfo

[http://pastebin.com/GvnRGpxG](http://pastebin.com/GvnRGpxG)

so.. what next.?

---

### Post by kalakohad on 2014-04-19
sometimes, explaining problem is 90% to the answer.

I noticed that moving mouse stopped flickering, so... bit google and i end up on that

[http://ubuntuforums.org/showthread.php?t=2173738](http://ubuntuforums.org/showthread.php?t=2173738)

and yes, that grub thing worked, i hope it helps someone else too:)

---

### Post by kbulatkin on 2014-05-18
[COLOR=#000000]Hello everyone,[/COLOR]
 
[COLOR=#000000]I had an annoying problem of cracking, crackling, distorted sound in browser based video players, such as on utube for example in Ubuntu 14.04 LTS .  Games and VLC/Other Ubuntu player worked fine.  After doing some research, I found this and other threads.  This is what fixed the issue for me.[/COLOR]

[COLOR=#000000]Run in terminal this command:  sudo gedit /etc/pulse/default.pa[/COLOR]

[COLOR=#000000]changed lines[/COLOR]

[COLOR=#000000]load-module module-udev-detect tshced=0

Rebooted.[/COLOR]

---

### Post by danieljohnhousley on 2014-05-26
> **kbulatkin said:**
> [COLOR=#000000]Hello everyone,[/COLOR]
 
[COLOR=#000000]I had an annoying problem of cracking, crackling, distorted sound in browser based video players, such as on utube for example in Ubuntu 14.04 LTS .  Games and VLC/Other Ubuntu player worked fine.  After doing some research, I found this and other threads.  This is what fixed the issue for me.[/COLOR]

[COLOR=#000000]Run in terminal this command:  sudo gedit /etc/pulse/default.pa[/COLOR]

[COLOR=#000000]changed lines[/COLOR]

[COLOR=#000000]load-module module-udev-detect tshced=0

Rebooted.[/COLOR]
 
I had exactly the same problem, and the solution you posted worked,  

My Alsa information before the fix was [http://www.alsa-project.org/db/?f=5329b31ebd9af346d48c3a00d359e63b3919656e](http://www.alsa-project.org/db/?f=5329b31ebd9af346d48c3a00d359e63b3919656e)

and after here [http://www.alsa-project.org/db/?f=7c4a4f2d217092cfa9d6b627effb560b87c77e73](http://www.alsa-project.org/db/?f=7c4a4f2d217092cfa9d6b627effb560b87c77e73)

EDIT: 
Actually that just minimized the choppy audio, a proper fix included making the grub changes here [http://ubuntuforums.org/showthread.php?t=2173738](http://ubuntuforums.org/showthread.php?t=2173738) as mentioned above.

however that introduced it's own problem of multiple keystrokes being reported at random intervals

---

