---
title: "kill process running XV overlay?"
date: 2007-12-12
forum: Programming Talk
---

### Post by segalion on 2007-12-12
I´m searching a command to discover the process PID that is using the XV overlay.

Sometimes firefox or rythmbox are using the XV videorender (that it is known to be used only by one program at a time), and when I run my favorite videoplayer it isnt able to get the XV overlay. I would like a script (myplayer) to kill all process using XV before running the player.

I have this script in order to:

>disable compiz - for better videoplaying support (OSD, changing overlay monitor and resize while playing, etc.).
>kill process running XV ?( thats what I need to ensure XV for my player)
>run player "$*"
>and then enable compiz again at exiting...


Please help me, I cant find anything (xvattr?, xvinfo? or something similar).

---

### Post by segalion on 2008-08-01
bump!!!

---

### Post by nvteighen on 2008-08-01
pidof is a command that prints the PID of a given process.
```

pidof firefox

```

But, of course, you need to know how the process is called.

---

### Post by opscure on 2008-08-01
You can get the pid right away if you run:
```
pid=$!
```
or you could grep out the process with 
```
ps aux|grep programName|grep -v grep
```
add a cut pipe to just return the pid

Throw it all in a bash script that kills compiz (probably need the pid for this too), kills mplayer, starts mplayer, and start compiz.

Probably should look something like this (use player and compiz instead of gedit and gcalctool):
```

#!/bin/sh
########set variables of pids
pid0=`ps aux|grep gedit|grep -v grep|cut -b 11-15`
pid1=`ps aux|grep calc|grep -v grep|cut -b 11-15`
########kill processes
kill -9 $pid0 2>/dev/null
kill -9 $pid1 2>/dev/null
########start up apps
gcalctool &
gedit &

```

---

### Post by pjwhite on 2008-08-01
I am suprised to hear that  you are only able to use Xv rendering by only one process at a time as I have been using vlc / xine and others to play up to 10 videos on the same computer. Granted the CPU and X ( GPU ) usage does go up, we get decent performance. 

I have also decoded 4 1920x1080 h264 videos with ffmpeg on a quad core!

---

### Post by segalion on 2008-08-04
Thakyou very mutch for your responses.
But I think that what I need is a command to discover the program that is using "XV video overlay". It is not related with pid, its related with X or videocard info.


If you write "xvinfo" you obtain info about the phisical adaptor of your card that can render video with hardware assisted.

Classical 2D engine has the best performance in my system (ATI Xpress 200M). Modern cards can use 3d render engine, that can render more than one at a time (i.e ati AVIVO system), but for me has not enough quality.
See my post [http://ubuntuforums.org/showthread.php?p=5501290#post5501290](http://ubuntuforums.org/showthread.php?p=5501290#post5501290)

---

