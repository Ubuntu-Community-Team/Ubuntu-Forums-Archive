---
title: "Ubuntu 16.04 LTS Memory Crash"
date: 2018-02-26
forum: New to Ubuntu
---

### Post by marimuria on 2018-02-26
[B]My Rig:
[/B]Heatsink: &#8203;Cooler Master Hyper 212
Ram: &#8203;Corsair Vengeance LPX 16GB
(2x8GB) DDR4 DRAM 2400MHz
Processor: &#8203;AMD Ryzen 7 1800X
Motherboard: &#8203;ASRock X370 TAICHI
Power Supply: &#8203;EVGA SuperNOVA 550
G3
Case: &#8203;Rosewill - Black ATX Full Tower
Gaming Computer Case - Throne-Window
Storage: &#8203;(6) WD Red 4TB NAS Hard
Disk Drive - 5400 RPM
(1) WD Blue 1TB
Graphics Card: Radeon HD 7450
OS: Ubuntu 16.04 LTS
Software: Plex Media Server 1.11.3.4803
I use the red drives in raid 10 using zfs. (Three mirrored pools). The Blue drive is my OS.
[B]
Problem:[/B] 
I understand [https://www.linuxatemyram.com/](https://www.linuxatemyram.com/) but... I notice that when I am watching movies over time, I will be using 8+ gb of memory, and when I use the command "sudo free mem" I will have a ton of memory "Used", but not very much cache.
For example: I will have 6gb of memory being used, and 4gb used as buff/cache which would make sense.... Then my memory will be at 9gb used and I will only have 1.5gb at buff/cache. I have had applications crash due to too much memory being 'used'. I have since then preformed "sudo apt-get upgrade" "sudo apt-get update" "sudo apt-get -f".

I am pretty new to Ubuntu, and am currently learning as I go


This computer is being used as my Plex Media server, and the only application that is running is Plex Media Server 1.11.3.4803 as well as team viewer so I can remote into the computer.

---

### Post by TheFu on 2018-02-26
An 1800x for plex?  Ouch.  Transcoding for 100 devices or just 100x more CPU than is needed?

No need to use sudo with free. Abusing sudo will get you into problems sooner than later.

Did you check the system logs?  Any issues should show up in there.  "ubuntu log files" will locate a how-to.

Team viewer?  ssh is the remote management tool for Unix systems.  If you need to remote into a system and you have 100Mbps connection or faster, you can use X/Windows remote tools using the X-forward ssh facility.  For slower connections, there is x2go, which also works over ssh. I've used x2go from 5 continents.  It is the least hassle, fastest, non-paid, remote desktop that I know.

ZFS can be a memory hog, if you enable the advanced features.

Learning Unix has a steep curve.  My best advice: [http://blog.jdpfu.com/2017/03/31/learning-linux-condensed](http://blog.jdpfu.com/2017/03/31/learning-linux-condensed) to get the most knowledge in the quickest way, in the right order.

You probably don't need to fix broken packages more than once every 3+ yrs.  Is that something necessary on your system?  It shouldn't be needed, unless something else is wrong.  System maintenance for Linux/Ubuntu: [https://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](https://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc) - though I'd use **apt** today, not apt-get. A few of the other things have changed since 2011 too, but those aren't too important.  Patching and doing versioned backups are the main things for system management on Linux.

---

### Post by marimuria on 2018-03-01
The 1800x is required for the number of streams that I use with my plex server. 2000 passmark score per 1080p stream is what is recommended, but I also have some 4k videos and higher bitrate 1080p video content.

I have stopped using sudo with free mem, I now understand to use the sudo command very sparingly.

When looking at the system logs, there are so many folders for the log files, I have a rough time understanding where to even start.

As far as team viewer is concerned, I use this because I dont want to deal with 100% Unix/Gnome interface. I prefer the GUI and more user friendly screen share that I have with team viewer. This is a key reason I picked the desktop version of Ubuntu, opposed to the server version.

I understand ZFS can take a large amount of memory, but I only have 2tb of data on the server at the moment, and the only feature I have is the raid configuration.

"You probably don't need to fix broken packages more than once every 3+ yrs. Is that something necessary on your system? It shouldn't be needed, unless something else is wrong. System maintenance for Linux/Ubuntu: [https://lifehacker.com/5817282/what-...on-my-linux-pc](https://lifehacker.com/5817282/what-...on-my-linux-pc) - though I'd use apt today, not apt-get. A few of the other things have changed since 2011 too, but those aren't too important. Patching and doing versioned backups are the main things for system management on Linux."
I have just built this system (roughly 2-3 months ago) and am just trying to get my system fully stable. I only tried to fix packages, update, and upgrade because I wanted to ensure that this wasn't something that I was going to be overlooking when trying to fix my memory issue. As far as system maintenance, patching, etc. I believe this should not be the problem as I have already tried updating my OS, and have recently installed the system as a whole. 

I still have the issue of memory continually being used until the system crashes as I experienced this today. When I view the processes on "GNOME System Monitor", I find that there is no program using more than 150mb of memory. Even with these processes being so low, I still experience crashes, and the only thing that I think can be the problem is the memory. My reason for this is that I can also use the same system monitor and view that 10.4gb of memory is being used, and I have 0 applications open besides team viewer to remote in, and Plex to run the server.

---

### Post by TheFu on 2018-03-01
Back to the RAM issue ... with a Ryzen, the motherboards are known to be picky about RAM. Is all the RAM installed on the motherboard "approved and tested" list?  Have your run MemTest86+ for 12+ hours yet?  Those would be my first steps.  Many Linux Boot ISOs have  that utility included, though it seems that Ubuntu stopped including it recently.  I have a need to run it on one of my systems today as well.

Everything below is "for example" stuff. Things I've learned over decades of Linux/Unix/Windows experience.

Linux will use RAM as disk and network buffers, as needed.

GUI system monitor tools will often lie about things.  Best to stay with CLI/shell commands. Plus, you can copy/paste the output here to get expert views. top/htop are favorites. There are subtle things to understand - refer to the manpage for each tool for the specifics.  **man top**

If your video content is h.264, then no transcoding should be needed for 99% of the playback devices. That makes the Plex server CPU performance nearly unimportant. It becomes an I/O for disk and networking issue.  Provided you used Intel PRO/1000 NICs and not the other cheaper NICs (like realtek), then most of the networking will be offloaded to the ASICs in the NICs and the CPU becomes less important.  2000 passmark per stream assumes worst-case.  I normally see 3% of CPU used for each stream here on a low-end CPU.

But if the content is mpeg2 or h.265 or some of the older xvid/divx, rm, or in other funny containers that current generation players don't support, then transcoding by plex will happen.  A chromecast is pretty picky about the content it will play, so is a roku. If the playback devices are raspberry Pis running Kodi or Plex clients, transcoding will be less likely, though I force transcoding for some older home videos from 10 yrs ago just to make the player happier.

All modern browsers are hogs for both RAM and CPU. Giving a browser some constraints for force better behavior is a good thing, IMHO.  **firejail** is a tool for that.

Here's my plex server RAM use:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           7.5G        1.7G        231M         47M        5.6G        5.4G
Swap:          3.6G        2.0G        1.6G
```
Notice how most of the RAM is used for buffers?
It has a $50 G3258 Pentium CPU (4 yrs old about 3800 passmarks) and easily streams 1080p to 4 devices concurrently.  h.264 is my default content with DTS/AC3 inside an MKV container. It also runs a few virtual machines and is the NFS server for the entire network here, among other things.  I don't use ZFS on it, and since it is just media, it doesn't have RAID. I use RAID on important things - like other virtual machine servers, but I'm migrating to sheepdog for storage replication - no more RAID at all in a few months. ;)  ZFS **is** a good idea for media storage to limit bit rot problems.

The active VM on that machine is an 18.04 alpha desktop.
```
$ virsh list
 Id    Name                           State
----------------------------------------------------
 4     u1804                          running
```

Yep.  Appears the VM is mostly swapped out now, since it was given 3G of RAM.  Windows RAM use and CPU use has warped requirements for many people.  Generally, if you don't use Windows, your RAM needs are 1/4 what you think you need.  IMHO. There are exceptions, but with DDR4 RAM costing 5x what it did 18 months ago, being correct on total RAM needs matters, at least to me.

Regardless, memtest86 and look up the RAM compatibility with the Ryzen motherboard is where I'd start. [https://www.reddit.com/r/Amd/comments/66ggjd/psa_about_ryzen_and_memory_compatibility/](https://www.reddit.com/r/Amd/comments/66ggjd/psa_about_ryzen_and_memory_compatibility/) is some interesting reading.

---

### Post by marimuria on 2018-03-02
Using AMD's memory comparability chart. My memory is in fact compatible with the Am4 slot. [https://www.amd.com/system/files/2017-06/am4-motherboard-memory-support-list-en_0.pdf](https://www.amd.com/system/files/2017-06/am4-motherboard-memory-support-list-en_0.pdf) my ram is CMK8GX4M1A2400C16,

$ free mem
              total        used        free      shared  buff/cache   available
Mem:       16421632     5021652      252284       18488    11147696    10865392
Swap:       8317948           0     8317948

This is my memory after 24-ish hours after a restart, and there has only been about 1-2 movies that have been played on the server. Later today I should be able to post this with a much higher system usage.

"[COLOR=#000000]If your video content is h.264, then no transcoding should be needed for 99% of the playback devices. That makes the Plex server CPU performance nearly unimportant. It becomes an I/O for disk and networking issue. Provided you used Intel PRO/1000 NICs and not the other cheaper NICs (like realtek), then most of the networking will be offloaded to the ASICs in the NICs and the CPU becomes less important. 2000 passmark per stream assumes worst-case. I normally see 3% of CPU used for each stream here on a low-end CPU.[/COLOR]

[COLOR=#000000]But if the content is mpeg2 or h.265 or some of the older xvid/divx, rm, or in other funny containers that current generation players don't support, then transcoding by plex will happen. A chromecast is pretty picky about the content it will play, so is a roku. If the playback devices are raspberry Pis running Kodi or Plex clients, transcoding will be less likely, though I force transcoding for some older home videos from 10 yrs ago just to make the player happier.[/COLOR]

[COLOR=#000000]All modern browsers are hogs for both RAM and CPU. Giving a browser some constraints for force better behavior is a good thing, IMHO. [/COLOR][B]firejail is a tool for that."
[/B]
My CPU is not necessarily the problem that I am encountering. [https://forums.plex.tv/discussion/comment/1625523#Comment_1625523](https://forums.plex.tv/discussion/comment/1625523#Comment_1625523) is a post regards to my CPU using plex, but this isnt an issue. Thus, there was never a problem.

To my knowledge everything is compatible, and there should be no broken packages, and everything should be up to date, and not be suffering from being neglected. I understand that my current ram, and CPU is a bit overkill for my current application (Only running plex, with 3-5 concurrent users), but I would like to have the ability to expand into other avenues that my server might be able to offer. 
I feel like my hardware being more than I need only further illustrates that there is an issue. I can use the command as I posted above to see my memory usage, and be using about 10gb of memory, but only have 1.5 as buff/cache. Looking at your example you provided, with 1.7gb being used, and 5.6gb as buff/cache. I can understand this being the numbers that I would get when I look at my memory due to memory being used as hard drive cache, but when I have 7gb of used memory, and then 2gb of cache when plex is the only thing open on the computer. I know there is an issue.

---

### Post by TheFu on 2018-03-02
Can't tell for sure due to formating, but isn't 11147696 ... 11G used for buffers?  Which is a non-issue in my book. Would be helpful to use *quotes* / *code tags* and **free -hm** to reduce human eyesight issues. I'm old and need all the help with forum formating that I can get. Please.

Did you run memtest? Results?

Is being compatible with AM4 the same as having the motherboard vendor for the specific motherboard list the RAM as compatible?

Also, it hasn't been clear ... is there a plex client running on the system too, or just plex server?  My system only runs the plex server. GUIs eat lots of resources.

---

### Post by marimuria on 2018-03-03
My system only runs the plex server. Currently my system seems to be running normal. I have been notified by someone who uses plex that 4k videos can create a memory leak on your server.

> 
```

$ free -hm
              total        used        free      shared  buff/cache   available
Mem:            15G        8.6G        324M         18M        6.8G        6.6G
Swap:          7.9G          0B        7.9G

```



"[COLOR=#000000]Is being compatible with AM4 the same as having the motherboard vendor for the specific motherboard list the RAM as compatible?"[/COLOR]
The ram being Am4 compatible means that it works with my CPU. Additonally, according to this article: "AMD Ryzen series CPUs (Raven Ridge) support DDR4 3200+(OC)/2933(OC)/2667/2400/2133 non-ECC, un-buffered memory" [https://www.asrock.com/mb/AMD/X370%20Taichi/#Specification](https://www.asrock.com/mb/AMD/X370%20Taichi/#Specification)

I will try the memtest overnight today as it seems it needs to be ran on boot.

If memtest doesn't find any problems, then I have narrowed the problem to plex transcoding files. If this is the case, then there are some file formats that cause plex to have a memory leak. I might need to manually clear the cache, but with this being a leak, I think the only solution is for me to restart the server.

---

### Post by TheFu on 2018-03-03
Thanks for trying to format. If you do a reply-with-quote, the prior stuff will be quoted, if that is your intent. Then you can remove the parts of text not needed.

Other media players would make external system() calls to ffmpeg to transcode files. That would limit the memory leak to that single process and it would be cleaned up when ffmpeg finished.

Restarting PMS will have the same effect. No need to reboot the system.  Just restart the daemon.  You could script that to happen at a specific time or whenever RAM use became larger than some amount.  If RAM runs out, systemd should restart it automatically. It shouldn't crash the box.  Other things to consider would be to disable the plex "analyze" mode which sucked huge amounts of storage to make FFWD and RWND images available.

You could pre-transcode the 4K videos to 1080p, since it seems plex is transcoding those for most devices anyway. That could delay the memory issue, assuming people could/would choose the non-4K files for playback.  Just an idea - though I probably wouldn't do it.

<rant>
If I could, I'd slap the Plex people who decided that long paths are a good idea. Who thought that having all the plex stuff under : 
```
/var/lib/plexmediaserver/Library/Application Support/Plex Media Server
```
is a good idea?  **/var/lib/pms** would work just as well. The added 3 loooonnnnnnggggg levels adds NOTHING for clarity, just wastes characters in a path. Try typing all that in on a screen keyboard for a raspberry pi? And don't get me started about having spaces in directory/file names. It adds unnecessary scripting issues.
</rant>

---

### Post by marimuria on 2018-03-03
> **TheFu said:**
> 

Other media players would make external system() calls to ffmpeg to transcode files. That would limit the memory leak to that single process and it would be cleaned up when ffmpeg finished.



Although I have been messing with the web application, which might be providing me the bulk of the issues. The only players that connect to the server are xbox's, and Plex Media players. Additionally, they are all on the same LAN, so they are all direct play unless there is an unsupported audio file. 

> **TheFu said:**
> 
Restarting PMS will have the same effect. No need to reboot the system. Just restart the daemon. You could script that to happen at a specific time or whenever RAM use became larger than some amount. If RAM runs out, systemd should restart it automatically. It shouldn't crash the box. Other things to consider would be to disable the plex "analyze" mode which sucked huge amounts of storage to make FFWD and RWND images available.


I need to do some looking around to find where my Plex daemon is located. This seems like the only solution until plex has a future update to fix this issue. (To add more information, the problem to my knowledge is from video down-scaling. ie: You are playing a 4k video on a system that only supports 1080p or 720p, and then instead of the computer trying to figure it out, plex till downscale the video even though its playing 4k quality.

> **TheFu said:**
> 
You could pre-transcode the 4K videos to 1080p, since it seems plex is transcoding those for most devices anyway. That could delay the memory issue, assuming people could/would choose the non-4K files for playback. Just an idea - though I probably wouldn't do it.


If there is a problem with memory leading when down-scaling videos (Noticeably at 4k), then why would you not use the optimization feature with plex. I will need to do some playing around, but if you're playing a 4k video on a non-native 4k client, then plex should choose the optimized file. I may be incorrect, but this is my understanding.

[IMG]https://imgur.com/a/So9db[/IMG]

---

### Post by TheFu on 2018-03-03
I don't have any 4K content. If I did, all of it would be transcoded for any of my players. THAT is how plex works.  There isn't any direct-play unless plex thinks the file can be played directly by the device. 
Downscaling **is** transcoding.  If the plex profile for a specific device is wrong, then it will transcode.  I've had that issue where it decided to transcode everything for a device that wasn't in the plex DB, until I made a profile for the device. It was a hassle.

Why do you need to know where the daemon is?  Just restart it using systemd. Should be painless.
```
sudo systemctl restart plexmediaserver.service
``` should be the command.  The old-school _server_ stuff should work on 16.04 too.```
sudo service plexmediaserver restart
```

You say there's a bunch of memory being used.  Does **top** show that for the process you think it is?  What about **vmstat**?  **Free** is handy to see overall RAM and swap use, but it doesn't help with details.

BTW, troubleshooting at this level isn't easy for someone new to Unix systems.  I would caution against copy/paste commands from online sources.  You really only want to use commands for Ubuntu 16.04.  If you have some time, getting a book that teaches Unix/Linux with a proper progression through the different skills will make your life much easier in the long term.  In the Linux works, GUIs change all the time - they are just another program, nothing special.  If you learn the CLI/shell method, that will usually work much longer.  I'm using shell scripts that I created in the early 1990s today. Plus, by using the shell, it is much easier to automate stuff, so the computer does things FOR you, not TO you. ;)

4 passes ... is that enough?  I usually have it memtest run 12+ hrs, at least.  It is such a hassle to have a system down here, that longer downtime to be certain is worth it. Your call. It is probably fine.

Not sure how much more I can help, if this was any help at all.  Seems the likely issue is plex transcoding in the same process and having a memory leak.  If it wasn't closed-source, we could do more, like run it through a memory checker. Alas, plex isn't open source, so we are stuck.

I use plex as a server only.  My clients run DLNA or Kodi. About a yr ago, I tried the plex client and found it unusable for my needs. We watch lots of movies with subtitles and need to pause to read sometimes. The plex controls would show at pause and block the subtitles. I've also setup both a SOCKS proxy and VPN server, so that no plex accounts are needed to access my content from anywhere in the world.  I've listened to my music from different continents this way. It is a nice solution.  For remote video, I usually just use the proxy (ssh rocks!) and reduce the playback to DVD quality when on travel. Of course, I'll usually take some video files with me to avoid internet abuse in hotels.

I wouldn't hold my breath waiting for a fix from Plex.

---

### Post by marimuria on 2018-03-03
I think I am determining the problem is with a codec being used on a client. Since posting this thread, I have not been able to replicate the memory leak (for better or worse). I have also stopped trying to watch a ridiculous amount of streams though the web app which plex bottlenecks anyway making this method obsolete. The only thing that would make sense to me at this point, is that there is a codec that when transcoded doesn't play well with plex. This then creates a memory leak problem that I have been experiencing above. I only have about four 4k videos at this time, and I have now created optimized versions for TV (8mb at 1080p). This also changes the audio playback, so hopefully this is a solution to the problem. 
In the future, I will probably optimize any 265, hevc video codecs. These seem to be very 'complicated' and often can be required to transcode to other clients. Unfortunately I don't have any definitive evidence to determine that this is a problem, but it should increase the performance of the server regardless.

Although I still am not 200% confident that I have this issue solved. You have given me a very solid foundation and I believe the only next step is to start learning about unix.

---

### Post by marimuria on 2018-03-03
> ```

$ free -hm
               total        used        free      shared  buff/cache   available
Mem:            15G        9.5G        4.0G         17M        2.1G        5.6G
Swap:          7.9G          0B        7.9G


```

I have tried restarting plex with 
> ```
$ sudo systemctl restart plexmediaserver.service
```
as well as the other method you described. This had 0 influence on my memory used. Not sure if there is something else going on.

---

### Post by TheFu on 2018-03-03
h.265 codecs have to be transcoded on all my playback devices. NONE support hardware decoding.  Unless you have very new devices, say less than 18 months old with the latest firmware, then stick with h.264 to avoid transcoding.  Just because the HW supports h.265, doesn't mean the plex profile for it is sending that format.

I have raspberry pi v2, v3, roku v3 and intel computers running Ubuntu. NONE support h.265 decoding in hardware. None of my GPUs support h.265 in hardware either.  This means that any h.265 content (or other flavors like hvec) have to be transcoded by plex, using software, to view those files.

It would help if you were clear about which part of plex is being used with mosts posts for help.
* plex server
* plex client (web/application)
* plex web interface
* DLNA - controller
* DLNA - renderer

In my environment, the DLNA controller and renderer are often on the same machine.  Even if these are all run on the same machine, they are communicating using network protocols.

Getting streams via the web should be the last resort choice, especially if you care about video quality. Browsers suck at video and eat RAM like it was a tic-tac.

---

### Post by marimuria on 2018-03-03
In reference to my second post with the code and picture. This is on the server, with only the plex server online. There was no plex clients online on this system. Additionally, A few days ago I disabled DLNA option as a plex server option as I dont need this. 

I am rather confused that the command did not clear any memory what-so-ever. I performed the command and it was if I didn't do anything.

---

### Post by TheFu on 2018-03-03
> **marimuria said:**
>  I am rather confused that the command did not clear any memory what-so-ever. I performed the command and it was if I didn't do anything.

What command, exactly? Best to be explicit here. Show the exact command and all output from it. Please use "code tags", so things line up.  We are used to seeing that output.

If you stopped something and memory use wasn't less, then you/we are looking at the wrong process.  What does **top** say is using all the RAM and swap?

Just because you aren't running anything, doesn't mean something else isn't running for maintenance in the background.  Unix is multi-user, even if there is only 1 user.

---

### Post by marimuria on 2018-03-03
I thought that I gave enough information, my apologies. 
I used the command:
```
$ free -hm              total        used        free      shared  buff/cache   available
Mem:            15G        9.3G        4.1G         17M        2.3G        5.8G
Swap:          7.9G          0B        7.9G

```

Using this, I can see that I am utilizing 9.3gb with 2.3gb of this being buff/cache. This Rather odd since most memory incentive processes is 78.2mb (TeamViewer_Desktop). 

The command I used to see if it would be a fix is:
```
sudo systemctl restart plexmediaserver.service
```
This command had no affect of the Used memory or the buff/cache shown above. 

When using **top** I see the following:
```

top - 19:42:48 up  9:05,  1 user,  load average: 0.04, 0.04, 0.00Tasks: 776 total,   2 running, 773 sleeping,   0 stopped,   1 zombie
%Cpu(s):  0.7 us,  0.2 sy,  0.0 ni, 99.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem : 16421632 total,  4204996 free,  9783472 used,  2433164 buff/cache
KiB Swap:  8317948 total,  8317948 free,        0 used.  6041748 avail Mem
```

---

### Post by marimuria on 2018-03-03
I forgot to say this, but the only process running is plex server, and team viewer.

---

### Post by TheFu on 2018-03-03
There are 50-150 processes running on any Linux system at a time.
Top should show all of those in a list ... below what you've posted, ordered by the processes using the most CPU and RAM.  For example:
```
top - 21:55:42 up 6 days, 14:11,  3 users,  load average: 0.37, 0.19, 0.32
Tasks: 268 total,   2 running, 266 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.8 us,  0.5 sy,  0.0 ni, 98.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  7871592 total,   126536 free,  1502808 used,  6242248 buff/cache
KiB Swap:  3780604 total,  1301596 free,  2479008 used.  5889500 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 2600 root      rt   0  142052  35592  23084 S   1.0  0.5  91:22.18 corosync    
   21 root      25   5       0      0      0 S   0.7  0.0  36:37.30 ksmd        
    7 root      20   0       0      0      0 S   0.3  0.0   6:23.53 rcu_sched   
 1051 root     -51   0       0      0      0 S   0.3  0.0  23:53.40 irq/27-eth0 
10624 libvirt+  20   0 5274748 935700   9044 S   0.3 11.9  36:30.74 qemu-syste+ 
20217 plex      35  15 1269640  25780   4104 S   0.3  0.3   0:34.50 Plex Scrip+
    1 root      20   0   38260   5652   3488 S   0.0  0.1   0:04.91 systemd     
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.04 kthreadd
```   Of course, your list will be a little different.  Mine is basically idle with only 1 stream being serviced.  See how there are 268 processes?  Yours says there are 778 processes, so you have a bunch more running that you know.  Any chance that Teamviewer has been hacked?  I know they had an issue last fall with people hacking into their clients.

---

### Post by marimuria on 2018-03-03
Hmm... Because I have 775 tasks total, and yours is 268. Is there anyway for me to fix this? I'm not really sure what is normal for ubuntu, but since I have about 3x more tasks than you. I would assume something is running that should not be. Or installed at least.

```

top - 22:41:35 up 12:03,  1 user,  load average: 0.16, 0.08, 0.02Tasks: 775 total,   1 running, 773 sleeping,   0 stopped,   1 zombie
%Cpu(s):  0.1 us,  0.2 sy,  0.0 ni, 99.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem : 16421632 total,  4181860 free,  9784488 used,  2455284 buff/cache
KiB Swap:  8317948 total,  8317948 free,        0 used.  6039940 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
12749 valhalla  20   0 1981872 121412  13760 S   2.6  0.7   0:10.13 TeamViewer+ 
 3646 root      20   0 2222208  25216  11252 S   1.7  0.2   4:53.09 teamviewerd 
 2852 root      20   0  428220  67580  42196 S   0.7  0.4   3:49.11 Xorg        
 2755 root      20   0  449300  16304  13632 S   0.3  0.1   0:29.43 NetworkMan+ 
 4507 valhalla  20   0  714668  27384  22092 S   0.3  0.2   0:00.21 indicator-+ 
 8739 plex      35  15 1793948  67456  11608 S   0.3  0.4   0:37.47 Plex Scrip+ 
12832 valhalla  20   0  660280  35756  28368 S   0.3  0.2   0:00.47 gnome-term+ 
12849 valhalla  20   0   42436   4388   3116 R   0.3  0.0   0:00.43 top         
    1 root      20   0  185436   6144   4080 S   0.0  0.0   0:01.20 systemd     
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.02 kthreadd    
    6 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 mm_percpu_+ 
    7 root      20   0       0      0      0 S   0.0  0.0   0:00.20 ksoftirqd/0 
    8 root      20   0       0      0      0 S   0.0  0.0   0:21.00 rcu_sched   
    9 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh     
```

---

### Post by TheFu on 2018-03-04
You and I have different needs. I make many decisions around not wasting RAM or CPU in all my system configs.  I don't have CPU or RAM to waste. You do.

I'm running a server release, not a desktop. Not having a GUI makes for a much lighter system - probably about 75% less system overhead just by NOT running a GUI for a home setup.

I wouldn't ever use teamviewer.  If you look at top, that is using about 4G of RAM alone. I strive to use solutions under my own control for everything possible. Heck, I even run my own email server. Basically, my use of "cloudy" stuff is minimal. Most things that others use in the cloud, I run versions here.

I don't use gnome-terminals. They are heavy, but full featured.  I learned using xterms and rvterms, which are much lighter - 25k vs 660k in RAM.  There are trade-offs, but it has been part of my workflow for over 20 yrs now.  For example, I have about 20 windows open on my desktop. 2 are Thunderbird and Firefox. The rest are xterms with 15 logged into other systems.

I don't use network-manager. For my non-trivial networking needs, I find it gets confused easily, so I do networking manually. All non-portable systems here have static IPs.  Portable systems get static IPs through DHCP reservations.  My systems all know how to find each other. I don't use avahi or nmb stuff.  It is pure IP stuff here.

So, if you look through the top output, I don't use most of the things eating RAM and CPU on your system.  I do have systemd, unfortunately. But that is the way all the big distros have decided to solve a problem that I've never had. We get the fallout for the  largest data center users needing a faster boot. I'm not a fan of systemd, but it is getting better every year. By 2020, it might be stable enough for production use. We can hope. ;)

---

### Post by marimuria on 2018-03-04
> **TheFu said:**
> You and I have different needs. I make many decisions around not wasting RAM or CPU in all my system configs.  I don't have CPU or RAM to waste. You do.

I'm running a server release, not a desktop. Not having a GUI makes for a much lighter system - probably about 75% less system overhead just by NOT running a GUI for a home setup.

I wouldn't ever use teamviewer.  If you look at top, that is using about 4G of RAM alone. I strive to use solutions under my own control for everything possible. Heck, I even run my own email server. Basically, my use of "cloudy" stuff is minimal. Most things that others use in the cloud, I run versions here.

I don't use gnome-terminals. They are heavy, but full featured.  I learned using xterms and rvterms, which are much lighter - 25k vs 660k in RAM.  There are trade-offs, but it has been part of my workflow for over 20 yrs now.  For example, I have about 20 windows open on my desktop. 2 are Thunderbird and Firefox. The rest are xterms with 15 logged into other systems.


Gotcha. I believe I currently over-reacted about my ram as I posted before. It seems that I stay at a steady 9.4gb used or so. But my cache used will still increase and decrease, and the total used will stay the same for awhile. 

I am still trying to learn all the bits and pieces that Ubuntu/Unix has to offer, so in the future I will probably turn to a might more light weight option such as the server release such as you have mentioned. Or if I want to stay GUI intensive, then install Freenas or something.

---

### Post by TheFu on 2018-03-04
FreeNAS is BSD, not Linux.  It is a VERY, VERY, different OS with very different goals.
If you want a lighter Ubuntu, Lubuntu or Xubuntu "minimal" would work for most people who don't want the kitchen-sink pre-installed.

Is Teamviewer really worth 4G of RAM?  Really? There are many alternatives that don't require trusting some external 3rd party.  I prefer the NX protocol for remote access when ssh isn't enough, but ssh meets 99% of my needs.  A few other alternative methods for using GUI applications ... [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) ... on the same LAN, remote X/Windows is nice for non-video stuff.  For outside the LAN, x2go is nice.  I've used it from 5 continents.  No need to trust a 3rd party and ssh is used for authentication, which means no-more-passwords!  On the internet, if we trust passwords for access, then we've already failed.

---

### Post by marimuria on 2018-03-04
The amount of resources that Teamviewer is consuming is rather annoying, I do agree. I am going to do some looking in to x2go. This seems similar to my application of how I was implementing Teamviewer.

> [COLOR=#000000]FreeNAS is BSD, not Linux. It is a VERY, VERY, different OS with very different goals.[/COLOR]

I understand FreeNAS is not Linux, but it has many of the similar options that I use with Linux. My Server at this time is used for Plex, and I would like to in the future be able to implement some virtual machines in the future. I primarily like FreeNAS due to the ease-of-use, but the most I use Linux, I may enjoy the customization and more manipulation I may have. I would just like to keep open minded, since I have relatively just started my own HomeLab

---

