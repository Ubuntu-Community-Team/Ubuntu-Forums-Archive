---
title: "Unclear high CPU usage"
date: 2020-08-08
forum: New to Ubuntu
---

### Post by maharramov on 2020-08-08
Hello Everyone!

About a month ago I installed Ubuntu 20 on my laptop. Until recently it was running very smoothly. But suddenly the CPU usage became very high and started to overheat. I have no experience yet to find out why. 

It is also strange that the System Monitor shows lower maximum CPU usage than that shown by the 'top' command.

[ATTACH=CONFIG]286640[/ATTACH][ATTACH=CONFIG]286639[/ATTACH][ATTACH=CONFIG]286637[/ATTACH]

The 'systemd-cgtop' command shows that the high CPU usage is caused by the main process.


[ATTACH=CONFIG]286638[/ATTACH]

Please help me to solve the problem.

Thanks!

---

### Post by TheFu on 2020-08-08
Please don't post images of text screens.  Just copy/paste the text here, inside code tags.  People wanting to help cannot easily copy/paste relevant parts of an image, but we can highlight parts when text is used.

Also, without seeing the actual command used, we don't know what program and program options are being used.
Whatever "main" is seems to be using about 40% of 1 CPU.  Kill that program.  main is a typical name used by a programmer who is extremely new to C programming.  I don't have any programs with that name on any of my systems.

Use **top**, **iotop**, **netstat**, **vmstat**, and the **free** commands to get a quick look at what's using all the CPU, RAM, networking and disk I/O on any Unix system. These are all text admin tools. Some have many different options, so depending on what you want to see, you may want to add some options.

I like **free -hm**, for example. Also like **netstat -tulpn |grep LISTEN|grep -v 127** to see which ports are used by services on a system.  Then I'd use **lsof** to track down the exact program using any specific port.
```
$ netstat -tulpn |grep LISTEN|grep -v 127
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 0.0.0.0:4713            0.0.0.0:*               LISTEN      1932/pulseaudio     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      -                   
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -                   
tcp        0      0 0.0.0.0:**6011**            0.0.0.0:*               LISTEN      -
```
What's that on port 6011?

```
$ sudo lsof |grep 6011
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/114/gvfs
      Output information may be incomplete.
sshd        2259                                tf   10u     IPv4              33591      0t0        TCP *:6011 (LISTEN)
sshd        2259                                tf   12u     IPv4            3743804      0t0        TCP regulus:6011->localhost:34400 (ESTABLISHED)
**hexchat**   135291                                tf    3u     IPv4            3743803      0t0        TCP localhost:34400->regulus:**6011** (ESTABLISHED)
hexchat   135291 135292 gmain                   tf    3u     IPv4            3743803      0t0        TCP localhost:34400->regulus:6011 (ESTABLISHED)
hexchat   135291 135293 dconf\x20               tf    3u     IPv4            3743803      0t0        TCP localhost:34400->regulus:6011 (ESTABLISHED)
hexchat   135291 135294 gdbus                   tf    3u     IPv4            3743803      0t0        TCP localhost:34400->regulus:6011 (ESTABLISHED)

```
Ah - hexchat.  That's an IRC client. Makes sense. I use IRC.  BTW, localhost and regulus are the same system.  Localhost resolves to 127.0.0.1 and regulus resolves to 127.0.1.1 when on the same machine.  Both those addresses are not public and cannot be accessed by any other systems. The machine is talking to itself.

After that, I check **top** and see hexchat isn't using any real CPU. It isn't in the first 30 CPU processes. On that system, no single process is using over 0.5% of a CPU.  On a different system, Firefox is using about 10% of a CPU with spikes into the 90% range.  There are also a number of virtual machines - those spike from time to time in top as needed:
```
top - 10:06:05 up 12 days, 23:53,  7 users,  load average: 0.27, 0.55, 2.64
Tasks: 595 total,   1 running, 441 sleeping,   0 stopped,   3 zombie
%Cpu(s): 13.9 us,  0.6 sy,  0.0 ni, 85.4 id,  0.1 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem : 32932596 total,  9377816 free, 16149832 used,  7404948 buff/cache
KiB Swap:  4460540 total,  2116000 free,  2344540 used. 15338860 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND             
** 8784 libvirt+  20   0 4476536 2.973g   5260 S _158.3_  9.5   3982:40 qemu-system-x86     **
  356 libvirt+  20   0 6461848 1.204g   7920 S   2.3  3.8 437:36.64 qemu-system-x86     
 8712 libvirt+  20   0 3383920 1.843g   6856 S   0.7  5.9 196:25.07 qemu-system-x86     
 8420 libvirt+  20   0 2344368 570848   5292 S   0.3  1.7 133:03.18 qemu-system-x86     
 9037 libvirt+  20   0 2305620 1.088g   5016 S   0.3  3.5 380:11.49 qemu-system-x86     
 9242 libvirt+  20   0 6025796 0.997g   5484 S   0.3  3.2 153:25.27 qemu-system-x86     
 9338 libvirt+  20   0 2202620 371884   5948 S   0.3  1.1  88:58.30 qemu-system-x86    
``` 
 
Usually a VM uses less than 10% of 1 CPU, unless a request to do work comes in. Sadly, Windows VMs tend to waste more of everything. They have gotten better, but are still hogs compared to Linux VMs.

See how I used "code tags" and highlighting to point stuff out?  Can't do that with images.

---

### Post by maharramov on 2020-08-08
> **TheFu said:**
> Please don't post images of text screens.  Just copy/paste the text here, inside code tags.  People wanting to help cannot easily copy/paste relevant parts of an image, but we can highlight parts when text is used.

Good point. I take note of this.

It is very strange that the 'top' command does not show that high CPU usage.
```
top - 16:43:35 up  2:50,  1 user,  load average: 2,85, 2,70, 2,61Tasks: 254 total,   3 running, 250 sleeping,   0 stopped,   1 zombie
%Cpu(s): 46,3 us,  9,5 sy,  0,0 ni, 43,7 id,  0,1 wa,  0,0 hi,  0,4 si,  0,0 st
MiB Mem :  15912,3 total,  10652,0 free,   2489,0 used,   2771,3 buff/cache
MiB Swap:   2048,0 total,   2003,5 free,     44,5 used.  12387,6 avail Mem 


    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                             
   3775 stardust  20   0   47092  12128  11480 R  20,1   0,1  30:00.74 main                                                
   3773 stardust  20   0   47092  12140  11496 S  19,6   0,1  30:00.83 main                                                
 629581 stardust  20   0 1579272 101480  63164 S   5,1   0,6   1:02.20 chrome                                              
   1501 stardust  20   0 5000432 290844 104948 S   4,7   1,8   5:07.77 gnome-shell                                         
   1121 stardust  20   0  843056  60256  41884 S   4,2   0,4   4:33.82 Xorg                                                
 629659 stardust  20   0 5651184 130224  90060 S   3,3   0,8   0:16.49 chrome                                              
   1983 stardust  20   0    7032   3568   3272 S   0,9   0,0   0:18.06 libinput-debug-                                     
   2034 stardust  20   0 1186748 690640  72372 S   0,9   4,2   1:23.00 Mailspring defa                                     
 629403 stardust  20   0 3093076 307128 132200 S   0,9   1,9   0:55.42 chrome                                              
 708644 stardust  20   0  973916  54936  40048 S   0,9   0,3   0:06.61 gnome-terminal-                                     
    267 root     -51   0       0      0      0 S   0,5   0,0   0:35.48 irq/51-DELL0786                                     
    927 root      20   0  134492  10172   9336 S   0,5   0,1   0:01.28 thermald                                            
 658354 stardust  20   0 5585384 134348  92736 S   0,5   0,8   0:09.45 chrome                                              
 850121 stardust  20   0   20608   3928   3272 R   0,5   0,0   0:00.05 top                                                 
      1 root      20   0  169076  12028   7308 S   0,0   0,1   0:12.06 systemd                                             
      2 root      20   0       0      0      0 S   0,0   0,0   0:00.00 kthreadd                                            
      3 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 rcu_gp                                              
      4 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 rcu_par_gp                                          
      9 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 mm_percpu_wq                                        
     10 root      20   0       0      0      0 S   0,0   0,0   0:01.72 ksoftirqd/0                                         
     11 root      20   0       0      0      0 I   0,0   0,0   0:10.25 rcu_sched                                           
     12 root      rt   0       0      0      0 S   0,0   0,0   0:00.50 migration/0                                         
     13 root     -51   0       0      0      0 S   0,0   0,0   0:00.00 idle_inject/0                                       
     14 root      20   0       0      0      0 S   0,0   0,0   0:00.00 cpuhp/0                                             
     15 root      20   0       0      0      0 S   0,0   0,0   0:00.00 cpuhp/1                                             
     16 root     -51   0       0      0      0 S   0,0   0,0   0:00.00 idle_inject/1                                       
     17 root      rt   0       0      0      0 S   0,0   0,0   0:00.64 migration/1                                         
     18 root      20   0       0      0      0 S   0,0   0,0   0:01.54 ksoftirqd/1                                         
     21 root      20   0       0      0      0 S   0,0   0,0   0:00.00 cpuhp/2                                             
     22 root     -51   0       0      0      0 S   0,0   0,0   0:00.00 idle_inject/2                                       
     23 root      rt   0       0      0      0 S   0,0   0,0   0:00.62 migration/2                                         
     24 root      20   0       0      0      0 S   0,0   0,0   0:01.26 ksoftirqd/2                                         
     27 root      20   0       0      0      0 S   0,0   0,0   0:00.00 cpuhp/3                                             
     28 root     -51   0       0      0      0 S   0,0   0,0   0:00.00 idle_inject/3                                       
     29 root      rt   0       0      0      0 S   0,0   0,0   0:00.65 migration/3                                         
     30 root      20   0       0      0      0 S   0,0   0,0   0:01.19 ksoftirqd/3                                         
     33 root      20   0       0      0      0 S   0,0   0,0   0:00.00 kdevtmpfs                                           
     34 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 netns                                               
     35 root      20   0       0      0      0 S   0,0   0,0   0:00.00 rcu_tasks_kthre                                     
     36 root      20   0       0      0      0 S   0,0   0,0   0:00.04 kauditd
```


But 'systemd-cgtop' does:

```
Control Group                                                                       Tasks   %CPU   Memory  Input/s Output/s
/                                                                                     806  **223.2**     5.1G        -        -
init.scope                                                                              1      -     5.6M        -        -
system.slice                                                                          102      -   454.0M        -        -
system.slice/ModemManager.service                                                       3      -     6.7M        -        -
system.slice/NetworkManager.service                                                     3      -    13.5M        -        -
system.slice/accounts-daemon.service                                                    3      -     4.5M        -        -
system.slice/acpid.service                                                              1      -   524.0K        -        -
system.slice/avahi-daemon.service                                                       2      -     1.8M        -        -
system.slice/bluetooth.service                                                          1      -     3.2M        -        -
system.slice/boot-efi.mount                                                             -      -    24.0K        -        -
system.slice/colord.service                                                             3      -    22.2M        -        -
system.slice/cron.service                                                               1      -     2.3M        -        -
system.slice/cups-browsed.service                                                       3      -     4.1M        -        -
system.slice/cups.service                                                               1      -     5.4M        -        -
system.slice/dbus.service                                                               1      -    25.4M        -        -
system.slice/dev-hugepages.mount                                                        -      -   192.0K        -        -
system.slice/dev-mqueue.mount                                                           -      -   112.0K        -        -
system.slice/gdm.service                                                                3      -     6.1M        -        -
system.slice/irqbalance.service                                                         2      -     1.4M        -        -
system.slice/kerneloops.service                                                         2      -     1.6M        -        -
system.slice/networkd-dispatcher.service                                                1      -    19.3M        -        -
system.slice/polkit.service                                                             3      -     7.2M        -        -
system.slice/rsyslog.service                                                            4      -     4.2M        -        -
system.slice/rtkit-daemon.service                                                       3      -   824.0K        -        -
system.slice/snap-canonical\x2dlivepatch-95.mount                                       -      -   432.0K        -        -
system.slice/snap-chromium-1244.mount                                                   -      -   164.0K        -        -
system.slice/snap-chromium-1260.mount                                                   -      -   200.0K        -        -
system.slice/snap-core-9436.mount                                                       -      -   232.0K        -        -
system.slice/snap-core-9665.mount                                                       -      -   100.0K        -        -
system.slice/snap-core18-1880.mount                                                     -      -   160.0K        -        -
system.slice/snap-core18-1885.mount                                                     -      -   108.0K        -        -
system.slice/snap-gnome\x2d3\x2d34\x2d1804-24.mount                                     -      -   248.0K        -        -
system.slice/snap-gnome\x2d3\x2d34\x2d1804-36.mount                                     -      -   228.0K        -        -
system.slice/snap-gtk\x2dcommon\x2dthemes-1506.mount                                    -      -   220.0K        -        -
system.slice/snap-snap\x2dstore-433.mount                                               -      -   244.0K        -        -
system.slice/snap-snap\x2dstore-467.mount                                               -      -   260.0K        -        -
system.slice/snap-snapd-8140.mount                                                      -      -   528.0K        -        -
system.slice/snap-snapd-8542.mount                                                      -      -   276.0K        -        -
system.slice/snap.canonical-livepatch.canonical-livepatchd.service                     14      -    27.6M        -        -
system.slice/snapd.service                                                             21      -    91.0M        -        -
system.slice/ssh.service                                                                1      -     2.7M        -        -
system.slice/swapfile.swap                                                              -      -   548.0K        -        -

```

---

### Post by TheFu on 2020-08-08
No idea what cgtop does. Ah - we have manpages so we can look up what a command does.
> systemd-cgtop - Show top control groups by their resource usage
That is for process containment. If you have less than 3 years of Unix experience, I'm almost positive that doesn't do anything useful for you.

```

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                             
   3775 stardust  20   0   47092  12128  11480 R  20,1   0,1  30:00.74 main                                                
   3773 stardust  20   0   47092  12140  11496 S  19,6   0,1  30:00.83 main
```

Did you figure out what "main" is?  
Where is it running from?  
Which package is it part of?
Is "main" running a network listener, i.e. a network service?  Is it communicating outside the machine to other systems on the internet?

Ask if you don't know how to determine those things. They are basic skills, but there are 50 different methods for each - except the last one.  I'd guess there are only 5 ways for that.

---

### Post by maharramov on 2020-08-08
I did not know I should figure out what "main" is. Because my main concern is the "**223.2%**" CPU usage and what I see in the "**Process Manager**". Btw. I tried to differentiate process "/" from "main", could not figure out.

---

### Post by Doug S on 2020-08-08
> **maharramov said:**
> It is very strange that the 'top' command does not show that high CPU usage.
```
top - 16:43:35 up  2:50,  1 user,  load average: [COLOR="#FF0000"]2,85[/COLOR], 2,70, 2,61Tasks: 254 total,   3 running, 250 sleeping,   0 stopped,   1 zombie
%Cpu(s): [COLOR="#FF0000"]46,3[/COLOR] us,  [COLOR="#FF0000"]9,5[/COLOR] sy,  0,0 ni, [COLOR="#FF0000"]43,7[/COLOR] id,  [COLOR="#FF0000"]0,1[/COLOR] wa,  0,0 hi,  [COLOR="#FF0000"]0,4[/COLOR] si,  0,0 st

```
But 'systemd-cgtop' does:

```
Control Group                                                                       Tasks   %CPU   Memory  Input/s Output/s
/                                                                                     806  **223.2**     5.1G        -        -
                                                           -      -   548.0K        -        -

```Actually, they don't disagree by much. Top shows the 1 minute load average as 2.85 or 285%. The other numbers are over a much shorter interval and out of all 4 CPUs, so the total of 56.3% * 4 = 225.2% (and yes, it can be annoying, attempting to determine when stuff is listed as out of 1 CPU or out of all CPUs.)

However, this is a digression from your real issue, which TheFu is helping with.

---

### Post by TheFu on 2020-08-08
> **maharramov said:**
> I did not know I should figure out what "main" is. Because my main concern is the "**223.2%**" CPU usage and what I see in the "**Process Manager**". Btw. I tried to differentiate process "/" from "main", could not figure out.

I don't have anything called "process manager" on any systems here, sorry. I didn't remove it, so it isn't a default for all flavors of Ubuntu.

/ isn't a process.  It is a control group inherited from the initial shell. We care about processes.  Multiple processes can be put into the same control group and I'd assume that any process not put into a specific control group would be in the / cgroup.    [https://en.wikipedia.org/wiki/Cgroups](https://en.wikipedia.org/wiki/Cgroups)  Windows doesn't have anything like this to my knowledge.

The process using the CPU is "main".

---

### Post by CatKiller on 2020-08-08
One way to find out about a particular process would be to see what your system says about that process. Since one of the instances you've shown has a Process ID of 3775, we'll go with that for the example.

```
cat /proc/3775/cmdline
```

will show the command line that was used to spawn process 3775. The files in /proc aren't really files, but you can use programs - like cat - as if they were files.

---

### Post by maharramov on 2020-08-14
Thanks Catkiller, your suggestion solved my problem. It was the Mailspring application.
Sorry my late reply. I was busy with daily responsibilities.

---

