---
title: "Quake servers running on background, Tmux."
date: 2014-05-05
forum: New to Ubuntu
---

### Post by wallace2 on 2014-05-05
Hello there!

PLEASE!! I need some help. I am new to Linux and I am actually proud to have made this far by myself..  I installed an Ubuntu 12.04 in a remote computer to run quakeone servers (T-Rex of cpu multiplayer) and I managed to put all the servers ON and running on background with nohup and on tmux. 

It´s quite painfull to find the waterfall of pendencies to install all libraries to get those servers running.. How do you guys cope with that?  Every single thing you need have 2000 dependencies and each one of that has another 2000 heehehe TIRING :) 

Well.. let´s go to what matters.

What do I need to do to bring this servers from background to foreground and split it? So I could have all the 5 servers in different screens to manage when I was here and when I have to logoff I put the servers in background again. 

I am using PUTTY. 

This is what I find when I type TMUX LS 

0: 1 windows (created Sun May  4 17:18:12 2014) [168x42] (attached)
1: 1 windows (created Sun May  4 17:20:01 2014) [80x23]
10: 1 windows (created Mon May  5 10:35:34 2014) [80x23]
11: 1 windows (created Mon May  5 10:36:46 2014) [80x22] (attached)
12: 1 windows (created Mon May  5 10:37:51 2014) [80x23]
13: 1 windows (created Mon May  5 10:38:02 2014) [80x22] (attached)
14: 1 windows (created Mon May  5 10:55:35 2014) [80x23]
15: 1 windows (created Mon May  5 10:59:06 2014) [80x22] (attached)
16: 1 windows (created Mon May  5 10:59:24 2014) [80x21] (attached)
17: 2 windows (created Mon May  5 11:01:55 2014) [80x23]
18: 1 windows (created Mon May  5 11:06:09 2014) [168x43]
19: 1 windows (created Mon May  5 11:31:57 2014) [168x45]
2: 1 windows (created Sun May  4 17:21:24 2014) [80x23]
20: 1 windows (created Mon May  5 14:31:39 2014) [168x43]
21: 1 windows (created Mon May  5 14:56:02 2014) [168x43]
22: 1 windows (created Mon May  5 19:10:38 2014) [168x43] (attached)
3: 1 windows (created Sun May  4 17:47:21 2014) [80x23]
4: 1 windows (created Sun May  4 17:50:08 2014) [80x22] (attached)
5: 1 windows (created Sun May  4 19:43:20 2014) [80x23]
6: 1 windows (created Sun May  4 19:45:18 2014) [80x23]
7: 1 windows (created Sun May  4 21:33:24 2014) [80x23]
8: 1 windows (created Sun May  4 21:36:51 2014) [80x22] (attached)
9: 1 windows (created Sun May  4 21:37:43 2014) [80x23]


Why do I have so many windows if I just have 5 servers up? How do I access those windows or close them if I dont need them? How can I identify my server, please?

This is the result of the command TOP


** 3676 root      20   0 18588 7092  260 S  7.9  1.4 123:17.93 pqlinux**
** 2487 root      19  -1 18592  960  236 S  7.3  0.2 127:31.91 pqlinux**
** 3047 root      20   0 18596 7972  388 S  7.3  1.6 125:28.34 pqlinux**
** 3310 root      20   0 18588 5996  276 S  7.3  1.2 125:08.29 pqlinux**
** 5363 root      20   0 18600 7340  220 S  7.3  1.5 113:00.71 pqlinux**
21923 root      20   0 85696 2904 1856 S  0.3  0.6   0:00.85 sshd
23989 root      20   0 17476 1448  972 R  0.3  0.3   0:00.08 top
    1 root      20   0 24320 1752  960 S  0.0  0.4   0:02.01 init
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S  0.0  0.0   0:03.21 ksoftirqd/0
    5 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kworker/0:0H
    7 root      RT   0     0    0    0 S  0.0  0.0   0:00.04 migration/0
    8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcu_bh
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/0
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/1
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/2
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/3
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/4
   14 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/5
   15 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/6
   16 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/7
   17 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/8
   18 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/9
   19 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/10
   20 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/11
   21 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/12
   22 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/13
   23 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/14
   24 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/15
   25 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/16
   26 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/17
   27 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/18
   28 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/19
   29 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/20
   30 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/21
   31 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcuob/22

The first 5 are my servers, the rest I dont know.

How can  I open one of the servers console, please?

Well, that´s it for now.. I have the servers running but I cant manage them :) 

Thanks in advance for any reply.

W3

---

### Post by mastablasta on 2014-05-06
the rest are system processes (root).

what are you trying to do? run 5 server simultaneously? why do you need tmux for that? what dependencies?

usually there are scripts or package managers that solve dependency issues.

---

### Post by wallace2 on 2014-05-06
Thanks !

As I am a newbie on Linux, I was researching on how to put jobs in background and for some reason I found tmux..

I am running 5 servers simultaneosuly..  

[B]3676 root 20 0 18588 7092 260 S 7.9 1.4 123:17.93 pqlinux
[B]2487 root 19 -1 18592 960 236 S 7.3 0.2 127:31.91 pqlinux
[B]3047 root 20 0 18596 7972 388 S 7.3 1.6 125:28.34 pqlinux
[B]3310 root 20 0 18588 5996 276 S 7.3 1.2 125:08.29 pqlinux
[B]5363 root 20 0 18600 7340 220 S 7.3 1.5 113:00.71 pqlinux
21923 root 20 0 85696 2904 1856 S 0.3 0.6 0:00.85 sshd
23989 root 20 0 17476 1448 972 R 0.3 0.3 0:00.08 top
1 root 20 0 24320 1752 960 S 0.0 0.4 0:02.01 init
[/B][/B][/B][/B][/B][B]As you can see above the first five pqlinux are my servers.  I don´t know how to get to their consoles again or to split each server console in  different windows.

HELP!

Thank you
w3[/B]**[B][B][B]**[/B][/B][/B]

---

### Post by mastablasta on 2014-05-06
ah i get it now -- this is a question about tmux actually since you are using it to handle various processes. hmm i do not know much about tmux, but their man pages should provide answer on how to run each process in their own "window". they are not actually windows as i understand tmux is ran entirely in terminal.

i can't help but wonder if something like using awesome or i3 would be easier to configure and maintain though all of them are X based. while you want to do it all in cli (terminal).

another option might be to use a web interface if you fail with tmux. have you checked this: [http://hyperpolyglot.org/multiplexers](http://hyperpolyglot.org/multiplexers)
so how about if oyu opened windows, run process opened another one run it there etc. until you have 5 each one running a quake server (as i understand this can be setup so it's done on boot). and then you can monitor or handle each server from it's own window. would that be a solution? you could then tile them arround as you prefer.

it seems GNu screens is another option (isnetad of tmux): [http://ubuntuforums.org/showthread.php?t=1460169](http://ubuntuforums.org/showthread.php?t=1460169)

---

### Post by wallace2 on 2014-05-06
Thanks mate!! I will check the webpage you have sent to me.

I have read the TMUX docs but I cannot make it work.. have tried, but it´s very confusing as I am still getting use to the linux console and commands. 

If annyone else know more about TMUX ... PLEASE SHED SOME LIGHT :) 



> **mastablasta said:**
> ah i get it now -- this is a question about tmux actually since you are using it to handle various processes. hmm i do not know much about tmux, but their man pages should provide answer on how to run each process in their own "window". they are not actually windows as i understand tmux is ran entirely in terminal.

i can't help but wonder if something like using awesome or i3 would be easier to configure and maintain though all of them are X based. while you want to do it all in cli (terminal).

another option might be to use a web interface if you fail with tmux. have you checked this: [http://hyperpolyglot.org/multiplexers](http://hyperpolyglot.org/multiplexers)
so how about if oyu opened windows, run process opened another one run it there etc. until you have 5 each one running a quake server (as i understand this can be setup so it's done on boot). and then you can monitor or handle each server from it's own window. would that be a solution? you could then tile them arround as you prefer.

it seems GNu screens is another option (isnetad of tmux): [http://ubuntuforums.org/showthread.php?t=1460169](http://ubuntuforums.org/showthread.php?t=1460169)

---

### Post by wallace2 on 2014-05-06
> **mastablasta said:**
> 
another option might be to use a web interface if you fail with tmux. have you checked this: [http://hyperpolyglot.org/multiplexers](http://hyperpolyglot.org/multiplexers)
so how about if oyu opened windows, run process opened another one run it there etc. until you have 5 each one running a quake server (as i understand this can be setup so it's done on boot). and then you can monitor or handle each server from it's own window. would that be a solution? you could then tile them arround as you prefer.



That´s what I did when I setup the 5 servers.. did it in 5 different putty windows. The problem I have is when I have to logoff I have to put the servers running in background to keep the task running and when I am back on I cannot reopen the 5 servers console on TMUX.. I can see them there, but I don´t know how to access it ..

HELP!

---

### Post by wallace2 on 2014-05-06
Anyone can help?

---

### Post by pork-chop7586 on 2014-05-07
I'm a noob myself, but I use screen on my Ubuntu server, which runs 2 minecraft servers and a teamspeak server, and I use screen to keep things running when I am away and I am able to recall their terminal locally or remotely as needed.

---

