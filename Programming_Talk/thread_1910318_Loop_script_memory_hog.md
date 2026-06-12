---
title: "Loop script memory hog"
date: 2012-01-16
forum: Programming Talk
---

### Post by Fenlig on 2012-01-16
Hey guys,
 
I wrote a script that sends a personal greeting to people who join my minecraft server :D only problem is that is uses up all memory on my server and then everything crashes :S
 
I would like to stick to shell as im only learning it now, but does anyone have any ideas on how to make my script more effective as well as pointing out why mine use so much memory?
 
log=/home/skay/minecraft_public/server.log
 
function proc {
runscript=`ps aux | grep minecraft_public | grep -v grep | wc -l`
}
 
while [ $runscript > 0 ] ; do
user=`tail -n 1 /home/skay/minecraft_public/server.log |grep "logged in" | awk '{print $4}'`
if [ $user > 0 ] ; then
screen -p 0 -S minecraft_public -X eval "stuff \"say Welcome to the server $user\"\015"
sleep 2
else
public proc
fi
done
 
 
Kind regards,
Fenlig

---

### Post by ofnuts on 2012-01-17
> **Fenlig said:**
> Hey guys,
 
I wrote a script that sends a personal greeting to people who join my minecraft server :D only problem is that is uses up all memory on my server and then everything crashes :S
 
I would like to stick to shell as im only learning it now, but does anyone have any ideas on how to make my script more effective as well as pointing out why mine use so much memory?
 
log=/home/skay/minecraft_public/server.log
 
function proc {
runscript=`ps aux | grep minecraft_public | grep -v grep | wc -l`
}
 
while [ $runscript > 0 ] ; do
user=`tail -n 1 /home/skay/minecraft_public/server.log |grep "logged in" | awk '{print $4}'`
if [ $user > 0 ] ; then
screen -p 0 -S minecraft_public -X eval "stuff \"say Welcome to the server $user\"\015"
sleep 2
else
public proc
fi
done
 
 
Kind regards,
Fenlig
What process(es) take up memory, according to your process manager? How many processes have you got?

---

### Post by Fenlig on 2012-01-17
Okay so when I run the script i monitored top and seen this.


Tasks: 663 total,   2 running, 659 sleeping,   1 stopped,   1 zombie
Cpu(s):  2.5%us, 15.6%sy,  0.0%ni, 81.7%id,  0.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  10253924k total,  4423616k used,  5830308k free,   219640k buffers
Swap:    18428k total,        0k used,    18428k free,   497164k cached
Change delay from 3.0 to: ^C
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1451 skay      20   0 2523m 591m 9964 S   18  5.9  22:20.58 java
 3071 root      20   0     0    0    0 S   11  0.0   0:04.84 kworker/0:0
   42 root      20   0     0    0    0 S    4  0.0   0:03.07 kworker/3:1
 4434 root      20   0     0    0    0 S    4  0.0   0:00.81 kworker/1:0
 1415 skay      20   0 2509m 1.2g 9968 S    3 12.4  53:11.59 java
   41 root      20   0     0    0    0 S    2  0.0   0:00.86 kworker/2:1
   44 root      20   0     0    0    0 S    1  0.0   0:00.53 kworker/5:1
 4827 skay      20   0 21864 1900 1088 R    1  0.0   0:00.14 top
 7465 skay      20   0 33508 8540  344 R    1  0.1   0:00.03 bash
 7324 skay      20   0 33300 8564  580 S    1  0.1   0:00.02 bash
 7329 skay      20   0 33308 8572  580 S    1  0.1   0:00.02 bash
 7334 skay      20   0 33316 8576  576 S    1  0.1   0:00.02 bash
 7339 skay      20   0 33324 8592  584 S    1  0.1   0:00.02 bash
 7344 skay      20   0 33332 8592  580 S    1  0.1   0:00.02 bash
 7349 skay      20   0 33336 8608  588 S    1  0.1   0:00.02 bash
 7354 skay      20   0 33344 8612  584 S    1  0.1   0:00.02 bash
 7359 skay      20   0 33352 8616  580 S    1  0.1   0:00.02 bash
 7364 skay      20   0 33360 8624  580 S    1  0.1   0:00.02 bash
 7369 skay      20   0 33368 8640  588 S    1  0.1   0:00.02 bash
 7374 skay      20   0 33372 8648  592 S    1  0.1   0:00.02 bash
 7379 skay      20   0 33380 8656  592 S    1  0.1   0:00.02 bash
 7384 skay      20   0 33388 8664  592 S    1  0.1   0:00.02 bash
 7389 skay      20   0 33396 8668  588 S    1  0.1   0:00.02 bash
 7394 skay      20   0 33408 8680  588 S    1  0.1   0:00.02 bash
 7399 skay      20   0 33416 8680  584 S    1  0.1   0:00.02 bash
 7404 skay      20   0 33420 8692  588 S    1  0.1   0:00.02 bash
 7409 skay      20   0 33428 8696  584 S    1  0.1   0:00.02 bash
 7414 skay      20   0 33436 8700  580 S    1  0.1   0:00.02 bash
 7419 skay      20   0 33444 8704  576 S    1  0.1   0:00.02 bash
 7424 skay      20   0 33452 8716  584 S    1  0.1   0:00.02 bash
 7429 skay      20   0 33456 8720  580 S    1  0.1   0:00.02 bash

---

