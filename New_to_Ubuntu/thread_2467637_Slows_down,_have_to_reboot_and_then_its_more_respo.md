---
title: "Slows down, have to reboot and then its more responsive."
date: 2021-10-02
forum: New to Ubuntu
---

### Post by cwmoser on 2021-10-02
Ubuntu 20.04.3 is very responsive but seems to slow down after I have used apps like Virtual Box or left a YouTube video open.
Even though I close those apps, Ubuntu remains slow until I reboot.
Its like something is continuing to consume resources slowing the OS down.

Any ideas?
How would one trouble shoot a situation like this?

---

### Post by ajgreeny on 2021-10-02
What hardware do you have, particularly RAM as this sounds like the system being short of available memory.
Both virtualbox and youtube running in a browser can use a lot of RAM.

Show us the oitput of command ```
inxi -Fzx
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by cwmoser on 2021-10-03
RAM = 16GB
CPU = Intel i7 quad core i7-2600

---

### Post by ajgreeny on 2021-10-03
So obviously not a RAM or straightforward resources problem with that hardware.
Please now show us the rest of your hardware with the output of ***inxi -Fzx*** which might give us other clues; perhaps graphics problems.

Next time it is running so slowly run terminal command ***top*** and see if you get any clues from the output of that.

---

### Post by cwmoser on 2021-10-03
```
$ inxi -Fzx
System:    Kernel: 5.4.0-88-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: MATE 1.24.0 
           Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:   Type: Desktop System: Hewlett-Packard product: HP Compaq 8200 Elite CMT PC v: N/A serial: <filter> 
           Mobo: Hewlett-Packard model: 1494 serial: <filter> BIOS: Hewlett-Packard v: J01 v02.06 date: 06/09/2011 
Battery:   Device-1: hidpp_battery_0 model: Logitech M705 charge: 90% status: Discharging 
CPU:       Topology: Quad Core model: Intel Core i7-2600 bits: 64 type: MT MCP arch: Sandy Bridge rev: 7 L2 cache: 8192 KiB 
           flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 54278 
           Speed: 1596 MHz min/max: 1600/3800 MHz Core speeds (MHz): 1: 1596 2: 1596 3: 1596 4: 1596 5: 1596 6: 1596 7: 1596 
           8: 1596 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Turks PRO [Radeon HD 6570/7570/8550] vendor: Hewlett-Packard 
           driver: radeon v: kernel bus ID: 01:00.0 
           Display: x11 server: X.Org 1.20.11 driver: ati,radeon unloaded: fbdev,modesetting,vesa 
           resolution: 1920x1080~60Hz, 1920x1080~60Hz 
           OpenGL: renderer: AMD TURKS (DRM 2.50.0 / 5.4.0-88-generic LLVM 12.0.0) v: 3.3 Mesa 21.0.3 direct render: Yes 
Audio:     Device-1: Intel 6 Series/C200 Series Family High Definition Audio vendor: Hewlett-Packard driver: snd_hda_intel 
           v: kernel bus ID: 00:1b.0 
           Device-2: AMD Turks HDMI Audio [Radeon HD 6500/6600 / 6700M Series] vendor: Hewlett-Packard driver: snd_hda_intel 
           v: kernel bus ID: 01:00.1 
           Sound Server: ALSA v: k5.4.0-88-generic 
Network:   Device-1: Intel 82579LM Gigabit Network vendor: Hewlett-Packard driver: e1000e v: 3.2.6-k port: f040 
           bus ID: 00:19.0 
           IF: eno1 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 4.09 TiB used: 969.34 GiB (23.1%) 
           ID-1: /dev/sda vendor: Western Digital model: WDBNCE5000PNC size: 465.76 GiB temp: 30 C 
           ID-2: /dev/sdb vendor: Western Digital model: WD1001FALS-00J7B0 size: 931.51 GiB temp: 41 C 
           ID-3: /dev/sdc vendor: Western Digital model: WD1002FBYS-01A6B0 size: 931.51 GiB temp: 56 C 
           ID-4: /dev/sdd vendor: Seagate model: ST2000NM0033-9ZM175 size: 1.82 TiB temp: 42 C 
Partition: ID-1: / size: 29.43 GiB used: 14.35 GiB (48.8%) fs: ext4 dev: /dev/sda1 
           ID-2: /home size: 388.21 GiB used: 228.81 GiB (58.9%) fs: ext4 dev: /dev/sda3 
           ID-3: swap-1 size: 7.81 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sdc2 
           ID-4: swap-2 size: 7.81 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sdb2 
           ID-5: swap-3 size: 8.00 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda2 
Sensors:   System Temperatures: cpu: 35.0 C mobo: N/A gpu: radeon temp: 47 C 
           Fan Speeds (RPM): N/A 
Info:      Processes: 269 Uptime: 1d 5h 54m Memory: 15.60 GiB used: 6.42 GiB (41.2%) Init: systemd runlevel: 5 Compilers: 
           gcc: 9.3.0 Shell: bash v: 5.0.17 inxi: 3.0.38
```

Its running fast and responsive when the above was taken.
When it slows down again, I'll post the output of $ top

While running OK, here is top:

```
$ top

top - 12:00:08 up 1 day,  5:56,  1 user,  load average: 0.75, 0.57, 0.34
Tasks: 268 total,   1 running, 267 sleeping,   0 stopped,   0 zombie
%Cpu(s):  3.9 us,  1.5 sy,  0.0 ni, 94.6 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :  15971.3 total,   5054.2 free,   6099.2 used,   4817.8 buff/cache
MiB Swap:  24192.0 total,  24192.0 free,      0.0 used.   9077.7 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                                                                    
 100274 carl      20   0 5306808   1.1g 414788 S  25.9   6.9 176:04.15 firefox                                                                                                                                    
   1210 root      20   0 1042804 217000 176968 S   8.0   1.3  30:06.49 Xorg                                                                                                                                       
 100371 carl      20   0 3863188   1.1g 342364 S   8.0   6.9 141:13.63 Web Content                                                                                                                                
  98221 carl      20   0  813896  95224  58448 S   2.3   0.6  10:30.99 compiz                                                                                                                                     
2644991 carl      20   0  404592  49820  38444 S   2.3   0.3   0:01.06 mate-terminal                                                                                                                              
 100428 carl      20   0 3839224 927156 202720 S   1.7   5.7  32:14.47 Web Content                                                                                                                                
 301476 carl      20   0 3434168 703484 155252 S   1.7   4.3  12:00.89 Web Content                                                                                                                                
 100478 carl      20   0 3213752 341896 160944 S   0.7   2.1  35:06.57 Web Content                                                                                                                                
 100573 carl      20   0   26.5g 179048  94264 S   0.7   1.1   3:35.73 WebExtensions                                                                                                                              
 100629 carl      20   0 4034812 605336 167776 S   0.7   3.7  28:41.99 Web Content                                                                                                                                
 284740 carl      20   0 3162300 508912 155012 S   0.7   3.1  13:10.19 Web Content                                                                                                                                
     10 root      20   0       0      0      0 I   0.3   0.0   0:44.78 rcu_sched                                                                                                                                  
   1048 root      20   0  238640   7992   6624 S   0.3   0.0   0:05.77 accounts-daemon                                                                                                                            
   1061 message+  20   0    9116   6124   3904 S   0.3   0.0   0:27.98 dbus-daemon                                                                                                                                
  97927 carl       9 -11 1671344  20976  16088 S   0.3   0.1   0:31.21 pulseaudio                                                                                                                                 
  98108 carl      20   0  162828   7780   7000 S   0.3   0.0   0:08.62 at-spi2-registr                                                                                                                            
  98194 carl      20   0  468996 101056  79932 S   0.3   0.6   0:11.23 wnck-applet                                                                                                                                
  98248 carl      20   0  848540  13076  10640 S   0.3   0.1   0:00.75 indicator-sound                                                                                                                            
  98343 carl      20   0  345220  24568  18444 S   0.3   0.2   0:05.96 mate-maximus                                                                                                                               
  98351 carl      20   0  313772   9216   7508 S   0.3   0.1   0:01.56 indicator-messa                                                                                                                            
  98571 carl      20   0  391008  41004  31856 S   0.3   0.3   0:15.20 gtk-window-deco                                                                                                                            
 100454 carl      20   0 3635960 430552 163328 S   0.3   2.6  17:28.26 Web Content                                                                                                                                
 301441 carl      20   0 2731184 247748 111888 S   0.3   1.5   2:32.91 Web Content                                                                                                                                
2551926 root      20   0       0      0      0 I   0.3   0.0   0:00.33 kworker/u16:1-events_power_efficient                                                                                                       
      1 root      20   0  168140  12004   8360 S   0.0   0.1   0:02.74 systemd                                                                                                                                    
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.07 kthreadd                                                                                                                                   
      3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp                                                                                                                                     
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par_gp                                                                                                                                 
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 mm_percpu_wq                                                                                                                               
      9 root      20   0       0      0      0 S   0.0   0.0   0:01.27 ksoftirqd/0                                                                                                                                
     11 root      rt   0       0      0      0 S   0.0   0.0   0:00.25 migration/0                                                                                                                                
     12 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0                                                                                                                              
     14 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0                                                                                                                                    
     15 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1                                                                                                                                    
     16 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/1                                                                                                                              
     17 root      rt   0       0      0      0 S   0.0   0.0   0:00.38 migration/1                                                                                                                                
     18 root      20   0       0      0      0 S   0.0   0.0   0:00.92 ksoftirqd/1                                                                                                                                
     21 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/2                                                                                                                                    
     22 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/2                                                                                                                              
     23 root      rt   0       0      0      0 S   0.0   0.0   0:00.38 migration/2                                                                                                                                
     24 root      20   0       0      0      0 S   0.0   0.0   0:00.87 ksoftirqd/2                                                                                                                                
     27 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/3                                                                                                                                    
     28 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/3                                                                                                                              
     29 root      rt   0       0      0      0 S   0.0   0.0   0:00.38 migration/3                                                                                                                                
     30 root      20   0       0      0      0 S   0.0   0.0   0:00.82 ksoftirqd/3                                                                                                                                
     33 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/4                                                                                                                                    
     34 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/4                                                                                                                              
     35 root      rt   0       0      0      0 S   0.0   0.0   0:00.40 migration/4
```

---

### Post by ajgreeny on 2021-10-03
How many tabs were open in firefox when you ran that **top** command, and was one of them running a youtube video?

25.9% CPU for firefox is pretty high I think; I currently have 4 tabs open, none of them youtube, and my CPU is using only between 1% and 6%.
If I run a youtube video it does rise to similar CPU usage as yours but is still not making the whole system run slowly.

I see from your inxi output that you have 3 swap partitions, one on each disk.
From your running Ubuntu can you show the output of command ```
free -mw
``` to ensure at least one of them is available for your Ubuntu installation, though I have to say that with 16G RAM swap is very unlikely to be used.

---

### Post by cwmoser on 2021-10-04
```

$ free -mw
              total        used        free      shared     buffers       cache   available
Mem:          15971        5110        5724         507         587        4548       10024
Swap:         24191           0       24191


```

I do often keep Firefox tabs open on paused YouTube videos.
Does that contribute to the slowness?

---

### Post by ajgreeny on 2021-10-04
> **cwmoser said:**
> ```

$ free -mw
              total        used        free      shared     buffers       cache   available
Mem:          15971        5110        5724         507         587        4548       10024
Swap:         24191           0       24191


```

I do often keep Firefox tabs open on paused YouTube videos.
Does that contribute to the slowness?
Yes, I think paused videos still use resources quite heavily, though if they were playing it would be higher.

It appears that all three swap files are in use, ie 3 × 8G which surprises me as i expected only the one swap to be used in the partition on which you have the running OS.

Can you please show the output of command ***mount | grep /dev/sd && swapon --show*** which may give more details of the situation.

---

### Post by bijayalaxmi1808 on 2021-10-04
I just assume that the system runs on a hard drive and when the apps are paged out to the swap space, then reading it back takes time and the whole system appears to be slow.
If that is the case then it's time to replace the hard drive with an SSD.

This was happening with me all the time when I install the OS on the hard drive. So, I moved the OS to the SSD and the whole world seems to be a lot faster now.

---

### Post by cwmoser on 2021-10-04
```

$ mount | grep /dev/sd && swapon --show
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
/dev/sda3 on /home type ext4 (rw,relatime,stripe=32748)
/dev/sdb3 on /home2 type ext4 (rw,relatime)
/dev/sdc4 on /media/carl/Home2-BACKUP type ext4 (rw,nosuid,nodev,relatime,uhelper=udisks2)
/dev/sdc1 on /media/carl/2714ef8e-ace9-4969-93ac-98fb2ff9cfc6 type ext4 (rw,nosuid,nodev,relatime,uhelper=udisks2)
/dev/sdc3 on /media/carl/Home-BACKUP type ext4 (rw,nosuid,nodev,relatime,uhelper=udisks2)
NAME      TYPE      SIZE USED PRIO
/dev/sdc2 partition 7.8G   0B   -2
/dev/sdb2 partition 7.8G   0B   -3
/dev/sda2 partition   8G   0B   -4

```

/dev/sda2 is the swap on my SSD boot drive. 

I did not realize I had 3 swap partitions until you asked me to run the swapon command.
Should I turn off swapping on the two non-SSD boot drives - sdb2 and sdc2?
How would I do that?

Thanks much for your help.

---

### Post by cwmoser on 2021-10-05
Of the three swap files, I went and disabled the two swap files on my non-SSD drives.
I now only have one swap and its on my SSD - /dev/sda2.
I edited the /etc/fstab file and commented out the two swap files.

Do you think I'm over working my SSD doing this?

---

### Post by mastablasta on 2021-10-05
remove swap partitions.

you can actually use a file as well.

with large amount of ram you can reduce the swapiness. more here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by cwmoser on 2021-10-08
I removed those 2 Swap partitions and now only have one Swap partition on my SSD.
Now after a couple days it seems to have indeed solved the slowness I was having.

---

### Post by ajgreeny on 2021-10-08
That's great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by cwmoser on 2021-10-09
> **ybelin77vbern said:**
> So what? did it work after all these manipulations? if yes. then let me know!


Yes, my Ubuntu OS now doesn't slow down.
I often keep paused YouTube videos and a VM in Virtual Box running, and before when I closed them because I felt the system was slow, it continued to feel slow, so I rebooted.  Doesn't have that problem so far.

---

