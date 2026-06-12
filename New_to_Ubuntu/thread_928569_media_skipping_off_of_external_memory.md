---
title: "media skipping off of external memory"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by danmeetswood on 2008-09-24
Howdy, so playing music or movies off of my USB external memory drive causes the playback to "kind of" stop every 40-60 seconds for about 4-6 seconds. It looks like it has stopped playback, but it picks up where it would be if it hadn't stopped. When this happens there is a surge of activity on the "System Monitor" applet, indicating about 50% or so usage of "IOwait." If anybody knows what to do to fix this it would be FANTASTIC.

---

### Post by Peter09 on 2008-09-24
It may be that you USB memory stick has just a slow transfer rate ... to slow to get the data across. However it is worth checking what else may be running. Use 'htop' - its in the repositories, to monitor the activity of your system

---

### Post by danmeetswood on 2008-09-24
Ok, well using this program while running music through exaile, it looks like "python exaile.py" (which there are four of running, that might be a problem) drops to 0% CPU usage after one of the processors rises to 100%, stopping playback, then quickly rises to 30-50% CPU usage, then down to about 15%. I'm not really sure what I should be looking for, however.

---

### Post by philinux on 2008-09-24
Try a different player.

---

### Post by danmeetswood on 2008-09-24
The same thing happens in Amarok (where there are also four "Amarokapp" applications running, so I'll assume having four is the norm *shrugs*)
I didn't have any problems running the audio files in VLC, but I would hate to not be able to use libraries while playing music.
Running video in VLC I get the same kind of problem. But not when I run them in Totem.
Am I just going to have to side-step my computer or is there a way to actually *fix* this? This hasn't always been a problem, just over the past month or two.

---

### Post by danmeetswood on 2008-09-24
scratch that. it just happens *less* when running them in the "working" programs.

---

### Post by philinux on 2008-09-24
I dont think it's normal to have 4 amarok players running at the same time. Something weird going on. I'd reboot then run system monitor and watch **processes** as you play a track.

---

### Post by danmeetswood on 2008-09-24
Well there's only one "amarokapp" that "System Monitor" detects. But using the "Htop" program that was recommended by peter09 earlier in the thread, it detects four processes with the same name, but different PIDs. Totem had eight, but is only one process in "System Monitor."

---

### Post by danmeetswood on 2008-09-24
;)
[IMG]http://www.nerdtests.com/images/badge/44a658cc2555e46e.gif[/IMG]

---

