---
title: "Why to use a Pid and Config file ?"
date: 2006-04-20
forum: Programming Talk
---

### Post by kolichina_s_s on 2006-04-20
Hi,

I am newbee in Linux and am working on C. I have developed a daemon, and I was able to launch it successfully and shut it down successfully. 

But when i studied the sample init script file of an existing daemon in init.d directory i found that most of them were using a .pid file from /var/run , while we should say good bye to the inital pid. why should i require this .pid file :rolleyes: ?

Also i want my daemon to be in any directory the user wants it to. but i have few problems as i am changing the current working directory of my daemon to a specified directory in my code. but i want my user to specify this directory. and also there are few more things that the user needs to specify. How can I achive this ? BTW what is config file and how can i use this file to suit my needs :confused:  ?

Please help in clearing these doubts.

Thanks in advance

---

### Post by LordHunter317 on 2006-04-20
[QUOTE=kolichina_s_s]But when i studied the sample init script file of an existing daemon in init.d directory i found that most of them were using a .pid file from /var/run , while we should say good bye to the inital pid. why should i require this .pid file :rolleyes: ?[/quote]So the system can stop your process without issue and trouble.  This is used by automated scripts, which don't have the ability of a human to figure out which instance of a process they need to kill.  Computers aren't good at guessing.

> Also i want my daemon to be in any directory the user wants it to.Actually, you probably don't.  What you want to do is allow them to specify directories to place things in at compile time.

> specify but i have few problems as i am changing the current working directory of my daemon to a specified directory in my code.Why? This seems somewhat unusual to me.

---

### Post by kolichina_s_s on 2006-04-20
[QUOTE=LordHunter317]So the system can stop your process without issue and trouble.  This is used by automated scripts, which don't have the ability of a human to figure out which instance of a process they need to kill.  Computers aren't good at guessing.
[/QUOTE]

Please tell me how can i create my own .pid file for use and what does this pid file contain in it ?

[QUOTE=LordHunter317]
Actually, you probably don't.  What you want to do is allow them to specify directories to place things in at compile time.
[/QUOTE]
I also need some username and passwd info to be given by the user which will be used in the daemon.

How to achieve the above ? is it through a Makefile ?

[QUOTE=LordHunter317]
Why? This seems somewhat unusual to me.
[/QUOTE]

Just to be on the safe side. BTW what is this **config file** ?

---

### Post by LordHunter317 on 2006-04-20
[QUOTE=kolichina_s_s]Please tell me how can i create my own .pid file for use and what does this pid file contain in it ?[/quote]It contains the PID of your master process, and nothing else.  

> How to achieve the above ? is it through a Makefile ?That would be one way.  Normally, people use autoconf or automake, which will create a special header file with all the necessary preprocessor macros for what you need to know.  You then hardcode paths based on those macros.

> Just to be on the safe side. BTW what is this **config file** ?Uhh, /etc/apache2/apache.conf is one.  So is /etc/vsftpd.conf.  Or /etc/sshd/sshd_config.  It's a file your daemon reads to allow it's behavior to be changed at runtime.  It can be in any reasonable format you want.

---

