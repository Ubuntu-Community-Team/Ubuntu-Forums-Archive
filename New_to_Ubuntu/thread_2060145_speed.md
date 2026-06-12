---
title: "speed"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by ericsonlouis on 2012-09-19
hey i am running ubuntu 21.04.1 and my laptop has 5 cores but it is not running as fast as it should be 
Any way you know i can speed it up?

---

### Post by cmont899 on 2012-09-19
What does your memory utilization look like?

```
free -m
```

---

### Post by vandorjw on 2012-09-19
What do you mean not running as fast as it should? 

I have never heard of a 5 core before. Please post results of:

```

cat /proc/cpuinfo

```

I will also assume that **21**.0.4.1 is a typo. **12**.0.4.1 

What exactly is slower than you expected?
Is your startup time slow?
Is program launch time slow?
Is the overal system slow when moving window frames around?

---

### Post by ericsonlouis on 2012-09-19
sry i mean 4 core

---

### Post by ericsonlouis on 2012-09-19
[IMG]http://[IMG]file:///home/junior/Pictures/Screenshot%20from%202012-09-19%2012:55:10.png[/IMG][/IMG]

---

### Post by synaptix on 2012-09-19
Can you provide us some more information on your system?

CPU make/model?
RAM?
HDD? SSD?
Video card? Drivers?
What DE? Unity3D? Unity2D? Other DE?

It's hard for anyone to help you out with very little information. :)

---

### Post by ericsonlouis on 2012-09-19
i have 300 free memory

---

### Post by vandorjw on 2012-09-19
Looks like you need more ram.
You can download some here.

[http://www.downloadmoreram.com/](http://www.downloadmoreram.com/)

:popcorn:

But in all seriousness, please post more system specifications.
There is a lot that can be done to speed up a computer...but there is nothing generic. If there was a single line of code, that could make all computers faster, regardless of hardware, it would be implemented on every single computer.

---

### Post by ericsonlouis on 2012-09-19
I have an i3 laptop 4 gigs of ram not sure what hdd is and not sure what video card or drivers i have and not sure what unity but i am running ubuntu 12.04.1 64bit version

---

### Post by ericsonlouis on 2012-09-19
> **cc7gir said:**
> Looks like you need more ram.
You can download some here.

[http://www.downloadmoreram.com/](http://www.downloadmoreram.com/)

:popcorn:

But in all seriousness, please post more system specifications.
There is a lot that can be done to speed up a computer...but there is nothing generic. If there was a single line of code, that could make all computers faster, regardless of hardware, it would be implemented on every single computer.



i have never heard of downloading ram b4

---

### Post by cmont899 on 2012-09-19
Sounds like the system is working pretty hard, only 300MB left out of 4GB. What is the output of the following command?

```
ps -eo pmem,pcpu,rss,vsize,args | sort -k 1 -r | head
```

---

### Post by ericsonlouis on 2012-09-19
%MEM %CPU   RSS    VSZ COMMAND
32.4 87.9 1278088 3075924 /usr/lib/virtualbox/VirtualBox --comment Windows 7 --startvm fedab248-6861-42bb-9c76-d8a3078de59e --no-startvm-errormsgbox
 2.6  0.1 104968 1195432 /usr/lib/libreoffice/program/soffice.bin --writer
 2.2  3.8 90428 1235276 compiz
 2.1  3.0 86120 626184 /usr/lib/chromium-browser/chromium-browser
 1.8  1.5 74628 907892 /usr/lib/chromium-browser/chromium-browser --type=renderer --lang=en-US --force-fieldtest=ConnCountImpact/conn_count_6/ConnnectBackupJobs/ConnectBackupJobsEnabled/DnsImpact/default_enabled_prefetch/GlobalSdch/global_enable_sdch/IdleSktToImpact/idle_timeout_10/Instant/AllControlA/Prefetch/ContentPrefetchPrefetchOn/Prerender/ContentPrefetchPrerenderNoUse1/ProxyConnectionImpact/proxy_connections_32/SpdyCwnd/cwndMin10/SpdyImpact/npn_with_spdy/SyncPromoLayoutExperiment/2/WarmSocketImpact/last_accessed_socket/ --channel=13817.4.1003282133
 1.5  0.0 61012 1026556 kmess -caption 'KMess' --icon kmess
 1.0  0.4 42156 1365568 nautilus -n
 1.0  0.4 40904 1055720 /usr/lib/virtualbox/VirtualBox
 0.8  3.0 32076 134600 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch

---

### Post by cmont899 on 2012-09-19
Stopping the windows VM would certainly help. If that's not an option install more ram and consider moving the VM to a dedicated hard drive or more preformant storage (SSD, HW raid, etc).

---

### Post by ericsonlouis on 2012-09-19
> **cmont899 said:**
> Stopping the windows VM would certainly help. If that's not an option install more ram and consider moving the VM to a dedicated hard drive or more preformant storage (SSD, HW raid, etc).

how do i mae the vm?

---

### Post by cmont899 on 2012-10-19
You should be able to stop the VM and move the VDI to other storage, make sure to update the path under the storage tab in the VM settings.

---

### Post by StinkySQL on 2012-10-19
> **cc7gir said:**
> Looks like you need more ram.
You can download some here.




I got a ewe ;(

---

