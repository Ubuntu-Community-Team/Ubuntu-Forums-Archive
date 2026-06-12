---
title: "Problems installing apps"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by i_have_a_sempron on 2008-04-28
I've been trying to install AppArmor and use Envy to get my video drivers working properly and I've been getting the same error with both.

```
~$ sudo apt-get install apparmor
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
~$


```

What do I need to do to fix this?

---

### Post by forestpixie on 2008-04-28
You can only have 1 instance of add/remove, synaptic, or anything in terminal using apt-get or aptitude at one time. Close one of them

---

### Post by i_have_a_sempron on 2008-04-28
Only apps I have running are firefox and amarok. I have rebooted my comp to see if that would help but it hasn't fixed anything for me. However, my process list is showing apt-get running on root. Is it possible that my computer has been infected with malware?

---

### Post by mgranet on 2008-04-28
That's odd. Maybe it's trying to download updates. Have you tried killing the running apt-get process, and then trying to install as normal? IIRC, KDE loads previous session by default. If that's the case, and you had apt-get running when you logged out, it might be starting on boot that way.

EDIT: Never mind. You said root, and I read it as boot. Yes, apt-get should be running as root. It needs administrative privs to install apps.

I never realized I had a reading problem until I started coming to the Ubuntu forums...

---

### Post by i_have_a_sempron on 2008-04-28
When I try to kill the process I get a message saying

Insufficient permissions to kill process 6332.

I'll try rebooting again.

---

### Post by mgranet on 2008-04-28
That probably won't help. As the process is root, you need to kill it as root. You will need to run the command
```
sudo kill 6332
```

assuming the PID is still 6332 after the reboot.

---

### Post by i_have_a_sempron on 2008-04-28
I rebooted my system, and it rebooted me into a text-only interface. I'm running of my live cd now. When I was in the text interface I tried commands like
enable kdm
kdm
and others off the top of my head and could not get the display manager turned back on....Also with this live cd, my touch pad doesnt work anymore. I had to go search my basement for a mouse lol. Anyone know how I can fix these problems?

---

### Post by mgranet on 2008-04-28
> **i_have_a_sempron said:**
> I rebooted my system, and it rebooted me into a text-only interface. I'm running of my live cd now. When I was in the text interface I tried commands like
enable kdm
kdm
and others off the top of my head and could not get the display manager turned back on....Also with this live cd, my touch pad doesnt work anymore. I had to go search my basement for a mouse lol. Anyone know how I can fix these problems?

```
startx
```

I'm guessing something half-installed, crashed, and this is how you ended up with these problems??

---

### Post by i_have_a_sempron on 2008-04-28
ok i tried rebooting again without the livecd this time and it wouldn't even get to the text interface. it stayed at this screen almost the entire time
> Squid Cache (version 2.6.STABLE18):Terminated abnormally.
CPU Usage: 0.008 Seconds=0.004 User+0.004 Sys
Maximum Resident Size: 0KB
Page faults with physical i/o:8
Aborted
FATAL:Could not determine fully qualified hostname, Please Set 'visible_hostname'

Squid Cache (version 2.6.STABLE18):Terminated abnormally.
CPU Usage: 0.004 Seconds=0.004 User+0.000 Sys
Maximum Resident Size: 0KB
Page faults with physical i/o:0
Aborted
                                              [Failed]

       *Starting anac(h)ronistic cron anacron [ok]
       *Starting deferred execution scheduler [ok]
       *Starting periodic command scheduler   [ok]
Not starting K Display Manager (KDM-KDE4);it is not the default display manager.
       *Running local boot scripts (/etc/rc.local/)
                                              [ok]

And it stays on that screen.

---

