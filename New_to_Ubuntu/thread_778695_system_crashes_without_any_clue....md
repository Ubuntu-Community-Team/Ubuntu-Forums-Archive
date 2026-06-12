---
title: "system crashes without any clue..."
date: 2008-05-02
forum: New to Ubuntu
---

### Post by kshtjsnghl on 2008-05-02
Hi

  I installed 8.04 over 7.10 3 days ago and i have been experiencing a lot of system hangs without any reason whatsoever.

 when i try to restart the application starting which my system got hanged the last time it does not show any problem. 

 I mean to say the crashes are quite random. Yesterday when i tried to play a video file in vlc player it hanged but after reboot when i again tried playing that file it showed no problem.

 Just about 5 minutes ago my system hanged when i was configuring ekiga softphone. i was playing some songs on exaile but they didnt stop .i could not initiate any process and i had to switch off the power supply directly.

 these are the some of the last results of ls -ltr /var/log

-rw-r--r-- 1 root   root  42184 2008-05-02 18:09 Xorg.0.log.old
-rw-r--r-- 1 root   root 376420 2008-05-02 18:19 udev
-rw-r----- 1 root   adm   31799 2008-05-02 18:19 dmesg
-rw-r----- 1 root   adm  373371 2008-05-02 18:19 acpid
-rw-rw-r-- 1 root   utmp 292292 2008-05-02 18:20 lastlog
-rw-r----- 1 syslog adm   78041 2008-05-02 18:20 auth.log
-rw-r--r-- 1 root   root 504063 2008-05-02 18:20 kdm.log
-rw-r--r-- 1 root   root  42107 2008-05-02 18:20 Xorg.0.log
-rw-r----- 1 syslog adm  657615 2008-05-02 18:20 kern.log
-rw-r----- 1 syslog adm  145395 2008-05-02 18:20 debug
-rw-r----- 1 syslog adm  339590 2008-05-02 18:21 syslog
-rw-r----- 1 syslog adm   79392 2008-05-02 18:21 daemon.log
-rw-r----- 1 syslog adm    5825 2008-05-02 18:21 user.log
-rw-r----- 1 syslog adm  542634 2008-05-02 18:21 messages
-rw-rw-r-- 1 root   utmp  61440 2008-05-02 18:22 wtmp


Is anyone else facing the same problem??
And what can be the solution.

---

### Post by Michael.Godawski on 2008-05-02
Try to boot into the old 22 kernel. This solved the crashes for me.

---

### Post by kshtjsnghl on 2008-05-02
hey my system did it again 

 i tried playing some file on vlc and it hanged and this time the log information is -

-rw-r--r-- 1 root   root 376830 2008-05-02 18:36 udev
-rw-r----- 1 root   adm   32085 2008-05-02 18:36 dmesg
-rw-r----- 1 root   adm  374384 2008-05-02 18:36 acpid
-rw-rw-r-- 1 root   utmp 292292 2008-05-02 18:38 lastlog
-rw-r----- 1 syslog adm   78503 2008-05-02 18:38 auth.log
-rw-r--r-- 1 root   root 597843 2008-05-02 18:38 kdm.log
-rw-r--r-- 1 root   root  41538 2008-05-02 18:38 Xorg.0.log
-rw-r----- 1 syslog adm  399262 2008-05-02 18:38 syslog
-rw-r----- 1 syslog adm  712132 2008-05-02 18:38 kern.log
-rw-r----- 1 syslog adm  155127 2008-05-02 18:38 debug
-rw-r----- 1 syslog adm   83785 2008-05-02 18:38 daemon.log
-rw-r----- 1 syslog adm    6124 2008-05-02 18:38 user.log
-rw-r----- 1 syslog adm  589024 2008-05-02 18:38 messages
-rw-rw-r-- 1 root   utmp  65280 2008-05-02 18:38 wtmp

By the way what is this wtmp. Both the times this was the last process..

---

### Post by kshtjsnghl on 2008-05-02
@Michael how do you boot in to the old 22 kernel??

---

### Post by cool_penguin on 2008-05-02
Hey. Did you update your Ubuntu 7.10 installation to 8.10 using web-update option? A clean Ubuntu install is usually the best way to go at least in my experience.

---

### Post by kshtjsnghl on 2008-05-02
I did the fresh 8.04 install and i dont know why is this happening. It is completely random...

---

### Post by cool_penguin on 2008-05-02
What are your system specifications?

---

### Post by kshtjsnghl on 2008-05-02
intel 945 gm chipset, 1.5 gb ddr2 ram, 60 gb hard disk intel media accelerator
And i am having 8.04 dual booted with windows vista...

---

