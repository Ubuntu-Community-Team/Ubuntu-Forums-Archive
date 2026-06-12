---
title: "What the **** is happening?!"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Pap3r on 2008-05-27
Just recently, today, I noticed my processor usage spike.  It stayed that way for a long time, so I restarted.  The problem went away until now.  I'm sitting at about 50% usage, with no programs saying they are taking any cpu.  Basically, I should be idling at 0%

Somehow though, I'm sitting at 50-70% constant for the last 10 minutes.  ps shows nothing abnormal, and I checked the system monitor, just in cse I was getting bad readings.  I also checked my network usage, just in case I was getting a ping flood. (ping -f)

I can not for the life of me figure out what is wrong.  It's as if I'm running F@H....  But I'm not.

EDIT
Oh, yeah.  I also see a connection on Firestarter to 78.148.127.191, form my ip, port 44778.  It's nothing I have seen before, so it seems alright.  Plus netcat shows nothing weird while nc -lvp 44778

---

### Post by jrusso2 on 2008-05-27
run top from the command line and when it spikes see whats using the cpu.  could be some index running.

---

### Post by spiderbatdad on 2008-05-27
try running top to see what is using cpu. or install htop for a better interface. Sounds like an indexing program running...trackerd or beagle.

---

### Post by tamoneya on 2008-05-27
also try to remove the system monitor from the top panel momentarily.  The system monitor can cause resource usage to be incorrect and can cause spikes as well.  It is much more accurate to use top as mentioned above.

---

### Post by Pap3r on 2008-05-27
Thanks for the UBER fast replies.  It's sudo...

EDIT

SO here's what I have tried.  I have tried pkill sudo and all variants from my account.  Then I opened a new session with ctrlaltf1 and logged in as root.  I tried pkill sudo, pkill 4950, killall sudo killall 4950, and they all acted as it they had succeeded.  None of them did.  How am I supposed to pkill sudo?

EDIT again

Got it, with ```
su
kill -9 4950
```

---

