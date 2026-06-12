---
title: "Strange problem with my UTStar 300 R2U router"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by mrdosa on 2008-04-28
Now this is something new. I am newbie so pardon me if I make some obvious mistakes. I use Ubuntu 7.10 and WinXP dual boot system. My ISP gives free unlimited download between 2am and 8am at 2mpbs! So I kinda  download a lot then. I wanted to schedule ubuntu to start automatically from hibernation mode at 2am and start downloading. But I couldnt. On xp I could use a software called WOSB which booted up the pc at 2am from hibernation. 
Last night for the first time I tried something new. I scheduled my net to be connect at 2:08am on Ubuntu [using sudo crontab, with command pon dsl-provider] and the torrent downloaded [deluge] to start at 2:10am [again using crontab]
Then I changed the menu.ls to make ubuntu the default OS. I then logged into XP and schedule the WOSB to wake up at 2am, and then hibernated windows. Thinking that the pc will wake up at 2am, log into ubuntu, and ubuntu will do the rest. 
Now here is what happened. The system did wake up at 2am, logged into ubuntu, and run the cron jobs. But it didnt connect to the net. When I checked the log files this is what I found:

Apr 29 03:15:37 mybuntu kernel: [ 4467.492519] NETDEV WATCHDOG: eth0: transmit timed out
Apr 29 03:15:40 mybuntu kernel: [ 4470.486657] eth0: Transmit timeout, status 0d 0000 c07f media 10.
Apr 29 03:15:40 mybuntu kernel: [ 4470.486663] eth0: Tx queue start entry 4  dirty entry 0.
Apr 29 03:15:40 mybuntu kernel: [ 4470.486666] eth0:  Tx descriptor 0 is 0008203c. (queue head)
Apr 29 03:15:40 mybuntu kernel: [ 4470.486669] eth0:  Tx descriptor 1 is 0008203c.
Apr 29 03:15:40 mybuntu kernel: [ 4470.486672] eth0:  Tx descriptor 2 is 0008203c.
Apr 29 03:15:40 mybuntu kernel: [ 4470.486674] eth0:  Tx descriptor 3 is 0008203c.


I searched for this online and here is what I found. but couldnt understand the head or tail of it:
[http://www.linuxquestions.org/questions/linux-networking-3/netdev-watchdog-eth0-transmit-timed-out-492159/](http://www.linuxquestions.org/questions/linux-networking-3/netdev-watchdog-eth0-transmit-timed-out-492159/)

And so here I am, asking for someone to help me out.
I need to use ubuntu for downloading, coz its fast and better. Thanks a lot.

---

### Post by hariprs on 2008-04-28
Are you able to connect to internet after this?

---

### Post by mrdosa on 2008-04-28
Some one please help!!!

---

### Post by mrdosa on 2008-04-28
In case it helps, I have been scheduling windows and auto running downloads for many months now. Never faced a problem there. I searched the net, and found people talking something about ACPI and stuff, and couldnt get a hold of it. Someone please help me out.

---

### Post by mrdosa on 2008-04-28
Yes. I am able to connect internet once I restart my ubuntu!!!

---

### Post by mrdosa on 2008-04-29
I had the same problem last night too. Can some atleast explain whats that I am doing wrong!?:confused:

---

### Post by hariprs on 2008-04-29
I don't know exactly about your problem.
But for scheduling your downloads you can use Flashget using wine.
It is working fine for me. But you need to keep your computer switched on. But you can put your network down and use cron to start your network after 2AM.

---

### Post by superprash2003 on 2008-04-29
yes.. hariprs is correct.The timeout seems to be because you are trying to connect as soon as you switch on ubuntu.. which doesnt give it time to realize its connections..

---

### Post by mrdosa on 2008-05-01
Well, I the problem is not about my scheduling. Its like this. If I hibernate my windows xp, and then boot up and log into ubuntu instead of windows [which remains in hibernation] I am not able to connect to the net. It says NETDEV timed out ...
Only if I restart windows does my eth0 come alive!!!

---

