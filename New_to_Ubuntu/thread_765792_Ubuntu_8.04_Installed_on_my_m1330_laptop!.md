---
title: "Ubuntu 8.04 Installed on my m1330 laptop!"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by doodio on 2008-04-24
Just did an install this afternoon, things are going fantastic!

This is such an upgrade from previous versions, almost everything worked right off the bat.

Issues:
Nvidia driver wouldn't kick in on it's own, could not use desktop effects!
Solution:
Downloaded EnvyNG and what a quick fix that was! Driver installed properly, set up the display and away I went. Full Desktop effects no problems!

Current Issues:
Microphone may not be working
aMSN and webcam seem to crash the system, but I have got the webcam to appear in setup...
Still trying to figure out volume control lol
Fingerprint reader doesn't work--> I heard there's a simple program to download and I will report back on that later.

MEDIA BUTTONS WORK NATIVELY!!! go ubuntu!

How I installed:

Via Vista Sp1 Business Edition--> Just put the disc in and installed no issues, very quickly too!
Setup:
Dell M1330
c2d T7500 2.2ghz
2GB Ram
160GB 7200rpm drive
Nvidia 8400G MS --> Works, install envy for drivers
Intel HD Audio -> Seems to work
Intel Wireless N - Works
Bluetooth - Works, not tested
0.3 slim led Webcam - Seems to work, crashed aMSN
media buttons - work



Here's an Ultra-newbie question for everyone:

So I'm up and running and quite happy so far, but I am concerned: How can I access all my files from Vista? Ie. My c: drive in Windows.
I've got lots of documents, mp3s and videos that I would like to access in Ubuntu.  Can this not be done because of the install method, ie it doesn't seem like a true dual boot.
When I go to mount stuff, mediadirect partion shows, recovery partition shows, and cd drive shows

CD drive and recovery mount fine
Mediadirect causes complete system freeze/halt.



One more issue: The computer is automatically scaling my processor speed to 800Mhz, and boosting to 2.2ghz when required. Is there a way to control how this performs when I'm plugged in or when I'm on battery. In vista I can switch to max performance and have a full 2.2ghz all the time.


Other remarks:
Fan is a bit louder and it's running hotter than it does in vista. Don't know why, but overall extremely pleased and will be keeping linux on my system, most likely as my primary OS once I test all my media playback.

---

### Post by doodio on 2008-04-24
Also, how can I use newsleecher on ubuntu... Or, is there a binary usenet alternative on linux? I can't seem to find one with the same capabilities.


Thanks!

---

### Post by riven0 on 2008-04-24
Regardin the cpu frequency thing, try this howto:


[How to change CPU frequency scaling in Ubuntu]("http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html")

I'm not sure what's wrong with the fan, but here's another howto if you haven't tried it already: [Dell laptop colling with i8kfangui]("http://ubuntuforums.org/showthread.php?p=4069092")

---

### Post by sam_delta on 2008-04-24
to read vista's files, go under places>computer in the top panel, and there ull have all devices/partitions, open your windows partition and copy files to ubuntu

sam

---

### Post by doodio on 2008-04-24
thank you, but it's not there!
CD-RW/DVD±RW Drive
Media Direct
Recovery
File System

Can't find windows...

any help is appreciated.

---

### Post by doodio on 2008-04-24
good news, I found it all in the /host directory

how strange :)

---

### Post by doodio on 2008-04-26
Off topic, I tried to use VirtualBox to install xp, but it doesn't really work in xp. Any help on how to set that up would be great. In xp, it just says device cannot start.

---

### Post by ckaga2000 on 2008-04-29
> **riven0 said:**
> Regardin the cpu frequency thing, try this howto:


[How to change CPU frequency scaling in Ubuntu]("http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html")

I'm not sure what's wrong with the fan, but here's another howto if you haven't tried it already: [Dell laptop colling with i8kfangui]("http://ubuntuforums.org/showthread.php?p=4069092")

I've upgraded to 8.04 from 7.10, and I too am having the CPU fan run like crazy with nothing actually running (< 10% According to gkrellm and top).

The fan sounds like what It was like in 7.10 when I had > 50% CPU load. I tried to follow that CPU Frequency how-to, but it says My Kernel is not configured correctly or the CPU does not support scaling. Any suggestions?

I can't find anything usefull on this via Google (This topic came the closest). At this rate I'll just have to back up my files and do a clean re-install of 7.10.

---

### Post by riven0 on 2008-04-30
> **ckaga2000 said:**
> I've upgraded to 8.04 from 7.10, and I too am having the CPU fan run like crazy with nothing actually running (< 10% According to gkrellm and top).

The fan sounds like what It was like in 7.10 when I had > 50% CPU load. I tried to follow that CPU Frequency how-to, but it says My Kernel is not configured correctly or the CPU does not support scaling. Any suggestions?

I can't find anything usefull on this via Google (This topic came the closest). At this rate I'll just have to back up my files and do a clean re-install of 7.10.

I'm guessing you're running an Intel Core Duo. You have to remove powernowd and install cpufreqd:

> sudo apt-get autoremove powernowd --purge

> sudo apt-get install cpufreqd cpufrequtils

Then add these modules to your /etc/modules file:

> cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace

Then reboot. Test whether it's working:
> 
cpufreq-info

And check for processor scaling:

> cat /proc/cpuinfo

Hopefully, that'll get you set up.

---

### Post by ckaga2000 on 2008-05-01
> **riven0 said:**
> I'm guessing you're running an Intel Core Duo. You have to remove powernowd and install cpufreqd:

No this is a Pentium 4 (Old Pavilion zd7000, geeze I forgot to put that in the original post. Must remember *preview twice, post once*). It's Single core, but I have hyper-threading enabled. I'm so used to seeing two CPU entries I forget that only I have two *virtual* CPUs.

Does this advice still apply?

Thanks for answering. I'm making note of all advice I'm getting, and I might have a go at upgrading again sometime soon. For now I just don't have the energy to noodle around with settings for various (unrelated) reasons, so I'm back at 7.10.

---

### Post by riven0 on 2008-05-01
> **ckaga2000 said:**
> No this is a Pentium 4 (Old Pavilion zd7000, geeze I forgot to put that in the original post. Must remember *preview twice, post once*). It's Single core, but I have hyper-threading enabled. I'm so used to seeing two CPU entries I forget that only I have two *virtual* CPUs.

Does this advice still apply?

Thanks for answering. I'm making note of all advice I'm getting, and I might have a go at upgrading again sometime soon. For now I just don't have the energy to noodle around with settings for various (unrelated) reasons, so I'm back at 7.10.

It should still work, but you may also want to add in p4_clockmod to your /etc/modules file and reboot. 

Waiting a while is probably the best option, though. Too many people are having problems with Hardy, which is shocking, this being the most painless installation for me. But I'm sure within a month or two all the bugs should be ironed out.

---

