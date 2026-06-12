---
title: "Hello....newbie here.  14.04 crashing and no way out apart from cold re-boot"
date: 2014-08-27
forum: New to Ubuntu
---

### Post by Steve_Guy on 2014-08-27
Hullo folks.  Really glad to be here!

Firstly, I haven't used Unix system (Solaris on Sparc station) since uni days in 1994 - got lazy and been using Windows.  However, just three days ago got a s/hand box (Intel Xeon 2.83GHz x 8, 15GiB mem) and thought...):P...bye bye Microsoft.  Downloaded Ubu 14.04 64-bit and set up with no real issues.  Filezilla/Google Chrome/Thunderbird/Firefox are only apps so far and they installed fine.

However, two screens and 4 open windows later, I am crashing approx every half hour or so with no warm re-boot possible.

Any ideas where I can start?

Btw - Steve & Guy are my first two real names......no attempt to be anything but me!

---

### Post by xxToxicGuyxx on 2014-08-27
what are the specs of ur pc or laptop just wanted to know cause you might be running out of ram [memory]

---

### Post by Steve_Guy on 2014-08-27
Hi.....15gb ram, so I doubt it

---

### Post by QIII on 2014-08-27
The amount of RAM was specified in the OP.

Steve_Guy:  did you run this machine at all with Windows and was its behavior acceptable?

---

### Post by Steve_Guy on 2014-08-27
s/hand box.....fully scrubbed when I bought it

---

### Post by QIII on 2014-08-27
OK.  One hardware bit I don't see is the graphics adapter.  What is that?

---

### Post by Steve_Guy on 2014-08-27
NVIDIA G84GL [Quadro FX 1700]

---

### Post by QIII on 2014-08-27
Good.  Best to have all of that.

Can you describe what happens when the machine crashes in some more detail?

---

### Post by Steve_Guy on 2014-08-27
windows freeze but cursor moves....for 30 secs or so, then that locks too.  Note: now been running trouble free for 40 mins (I am now timing between crashes).  Apps running: terminal & Chrome (with 5 tabs open).  Might try running a few more things & see what happens..

---

### Post by QIII on 2014-08-27
Good.  See if you can get a repeatable sequence in a few trials.  That might be helpful.

---

### Post by Steve_Guy on 2014-08-27
ok.....thanks for your advice.  I'll let you know.  gonna try some app combinations.......now 50 mins with no issues.  Typical!

I'm in the UK, so only going to be up for another two hours or so before shut-eye

---

### Post by wildmanne39 on 2014-08-27
This should help to reboot if it happens again so you do not have to do a hard reboot.
[http://blog.kember.net/articles/reisub-the-gentle-linux-restart/](http://blog.kember.net/articles/reisub-the-gentle-linux-restart/)

Also the next time it freezes look at the log files with these commands to see if you can narrow it  down.

```
sudo tail -n100 /var/log/syslog
sudo tail -n100 /var/log/kern.log
```

---

### Post by Steve_Guy on 2014-08-27
cheers Wild Man...& QIII

update - 01:06 hrs and no hitch

logs seem the best way to go rather than bouncing in and out of apps I have to say

seems as though I am in good company ;)

will update when I can

---

### Post by wildmanne39 on 2014-08-27
There are many people here that can read the log files, I am probably not going to available long, I am drinking stuff to prepare for two surgical procedures in the morning so I have my hands full.

---

### Post by Steve_Guy on 2014-08-27
Thanks...and I hope tomorrow goes well.

---

### Post by Steve_Guy on 2014-08-31
Warm re-boot (Alt+SysRq while slowly typing REISUB) is now working great.  Now time to tackle all the other stuff that's going on.

---

