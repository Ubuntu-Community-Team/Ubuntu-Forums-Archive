---
title: "acpid:exiting error during shutdown"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by rkm2008 on 2008-11-19
I just installed UBUNTU 8.10 on my ACER Travelmate 4500. It hangs with **acpid:exiting** when I shutdown. However it does not create problem when I restart. Could some one help?

---

### Post by Jerk1 on 2008-11-27
I am gettingthe same error when I try shutting down my tower. ASUS board, 2.4GHZ dual core Intel, Nvidia card. My laptop is having shut down issues as well, I see on the forums there are many other related issues. Please address, I really want to go to ubuntu full time and just ditch windows altogether, but this kind of stuff worries me in a supposed "final" release

---

### Post by Michael.Godawski on 2008-11-27
Might be linked with this bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995)

Possible workaround:
Open the file  /etc/init.d/alsa-utils with root privileges: 
```
gksudo gedit /etc/init.d/alsa-utils
```
Search for the  "stop)" entry, somewhere near line 353 . Add these lines, accordingly to your network names:

```
ifconfig wlan0 down
ifconfig eth0 down
```
In the end it should be something like this:
```
stop)
ifconfig wlan0 down
ifconfig eth0 down
EXITSTATUS=0
```
Save the file and try to shutdown.

---

### Post by Jerk1 on 2008-11-27
Excellent, thank you very much. Now I no longer get the acpid:exiting notification, I only get a cursor flashing endlessly and a computer that I have to hold the power button down for 5 seconds on to force it to shut off. In that respect it is behaving just like my laptop now. That would be lateral progress, which, I suppose, is at least some type of progress

---

### Post by Scywrath on 2009-02-09
I also experienced this on 8.10 64-bit. In my case VPN-connection seemed to cause the problem, so after "stop)" I added "ifconfig ppp0 down" to /etc/init.d/alsa-utils, and now it's fine.

---

### Post by jay4e on 2009-02-16
worked fine for me also.

jerk1: did you add all your network connections? on a desktop mb it should likely just be eth0 (and eth1 if your board has 2 nics).  if so then likely something else is hanging up your shutdown.  try checking the logs and see what the last thing the system did before you had to do a hard restart.

before shutdown note the time. do your shutdown and then hard shutdown after giving it 10-15 min to log any errors and be sure the cache is writen to disk.  wait a bit more and restart.  the check system>admin>system log and see what happened at the time just before the hard shutdown.

---

### Post by longtom on 2009-03-04
I'm feeling really supid...again.

How do I find out my Network names?  Would that be "Windows Network" and "Workgroup" as indicated in Nautilus?
Any other way to find out what the names are I would need?

My error messages are after shutdown or restart:

```

acpid: exitig

[1301.536017] CIFS VFS: server not responding
[1303.536053] CIFS VFS: No response for cmd 50 mid 95

...

```

and so it goes on.

I would like to try above workarround (also I'd love a fix rather), but need to be sure about my network names.

Any suggestion is appreciated

regards

longtom

---

### Post by CR34M3 CR4CK3R on 2009-03-09
Hi,

I have the same **ACPID: exiting** problem with my Pentium D desktop. The problem started after I installed the Novel Client for Ubuntu ([http://ubuntuforums.org/showthread.php?t=459717](http://ubuntuforums.org/showthread.php?t=459717)), so I think its safe to say that its definitely a network related problem.

I have tried Michael's work-around (using my only connection, eth0) but end up with the same problem as Jerk1.

My Acer laptop is running the same version of Ubuntu but has no such problems. I have yet to install the Novel Client on it...

I don't restart this pc much, but after some updates restarts are required and I'd very much like to fix this problem. Anyone else have some ideas?

---

### Post by longtom on 2009-03-09
> **CR34M3 CR4CK3R said:**
> Hi,

I have the same **ACPID: exiting** problem with my Pentium D desktop. The problem started after I installed the Novel Client for Ubuntu ([http://ubuntuforums.org/showthread.php?t=459717](http://ubuntuforums.org/showthread.php?t=459717)), so I think its safe to say that its definitely a network related problem.

I have tried Michael's work-around (using my only connection, eth0) but end up with the same problem as Jerk1.

My Acer laptop is running the same version of Ubuntu but has no such problems. I have yet to install the Novel Client on it...

I don't restart this pc much, but after some updates restarts are required and I'd very much like to fix this problem. Anyone else have some ideas?

[This](http://ubuntuforums.org/showthread.php?t=293513) finally did it for me!:D

Good luck

longtom

---

### Post by CR34M3 CR4CK3R on 2009-03-09
Thanks longtom, but that didn't work for me. Although it gave me insight as to what my problem is; if network drives are still mounted at shutdown (in my case, mounted via Novel Client) then the acpid error/stall occurs.

When I haven't run Novel Client or when I unmount drives before shutdown, the problem doesn't occur.

I'll tinker around some and see if I can get the auto unmounting thing to work...

---

### Post by Roasted on 2009-03-25
Just to note, I tried this with a Lenovo R500 and it worked perfectly.

Thank you.

---

### Post by herovazy on 2009-05-17
> **Michael.Godawski said:**
> Might be linked with this bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995)
 
Possible workaround:
Open the file /etc/init.d/alsa-utils with root privileges: 
```
gksudo gedit /etc/init.d/alsa-utils
```
Search for the "stop)" entry, somewhere near line 353 . Add these lines, accordingly to your network names:
 
```
ifconfig wlan0 down
ifconfig eth0 down
```
In the end it should be something like this:
```
stop)
ifconfig wlan0 down
ifconfig eth0 down
EXITSTATUS=0
```
Save the file and try to shutdown.
 
 
i'd had try this but it doesn't work with my computer.
I've got an Asus m3n78 with an AMD Phenom X4, a NVidia GeForce 9600GT and 3GB memory but the computer doesn't shut down at all.
 
can anybody help me?

---

### Post by rCXer on 2009-09-05
> **Michael.Godawski said:**
> Might be linked with this bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995)

Possible workaround:
Open the file  /etc/init.d/alsa-utils with root privileges: 
```
gksudo gedit /etc/init.d/alsa-utils
```
Search for the  "stop)" entry, somewhere near line 353 . Add these lines, accordingly to your network names:

```
ifconfig wlan0 down
ifconfig eth0 down
```
In the end it should be something like this:
```
stop)
ifconfig wlan0 down
ifconfig eth0 down
EXITSTATUS=0
```
Save the file and try to shutdown.

This also worked for me. Thanks :)

---

