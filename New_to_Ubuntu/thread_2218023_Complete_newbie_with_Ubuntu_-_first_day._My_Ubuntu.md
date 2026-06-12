---
title: "Complete newbie with Ubuntu - first day. My Ubuntu is slow...need to diagnose"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by Chris_Sabian on 2014-04-19
just installed the latest 14.04 LTS -32 bit version. I feel there is some lag....it's not that fast.  I am sure it needs tweaking, but i dont know how to diagnose the problems or fix them.  Anyone can systematically show me what to do?

I have an old computer

Gateway MX 6437
2 GB of RAM
 description: CPU
       product: AMD Turion(tm) 64 Mobile Technology ML-32
size: 1800MHz
       capacity: 1800MHz
       width: 64 bits
       clock: 200MHz

```
top - 08:21:02 up  1:46,  4 users,  load average: 0.75, 0.94, 1.21
Tasks: 185 total,   1 running, 184 sleeping,   0 stopped,   0 zombie
%Cpu(s): 42.5 us, 14.3 sy,  1.1 ni, 40.4 id,  1.6 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem:   1998152 total,  1621844 used,   376308 free,    29020 buffers
KiB Swap:  2031612 total,    16872 used,  2014740 free.   777188 cached Mem


  PID USER      PR  NI    VIRT    RES    SHR S %CPU %MEM     TIME+ COMMAND                                                               
13443 ari_ron+  20   0    5580   1340    952 R 17.9  0.1   0:00.04 top                                                                   
12790 root      20   0       0      0      0 S  6.0  0.0   0:02.62 kworker/0:2                                                           
    1 root      20   0    4568   2188   1360 S  0.0  0.1   0:03.24 init                                                                  
    2 root      20   0       0      0      0 S  0.0  0.0   0:00.00 kthreadd                                                              
    3 root      20   0       0      0      0 S  0.0  0.0   0:02.30 ksoftirqd/0                                                           
    5 root       0 -20       0      0      0 S  0.0  0.0   0:00.00 kworker/0:0H                                                          
    7 root      20   0       0      0      0 S  0.0  0.0   0:09.26 rcu_sched                                                             
    8 root      20   0       0      0      0 S  0.0  0.0   0:00.00 rcu_bh                                                                
    9 root      rt   0       0      0      0 S  0.0  0.0   0:00.00 migration/0                                                           
   10 root      rt   0       0      0      0 S  0.0  0.0   0:00.08 watchdog/0                                                            
   11 root       0 -20       0      0      0 S  0.0  0.0   0:00.00 khelper                                                               
   12 root      20   0       0      0      0 S  0.0  0.0   0:00.00 kdevtmpfs                                                             
   13 root       0 -20       0      0      0 S  0.0  0.0   0:00.00 netns                                                                 
   14 root       0 -20       0      0      0 S  0.0  0.0   0:00.00 writeback                                                             
   15 root       0 -20       0      0      0 S  0.0  0.0   0:00.00 kintegrityd                                                           
   16 root       0 -20       0      0      0 S  0.0  0.0   0:00.00 bioset                                                                
   17 root       0 -20       0      0      0 S  0.0  0.0   0:00.14 kworker/u3:0                                                          
   18 root       0 -20       0      0      0 S  0.0  0.0   0:00.00 kblockd                                                               
   19 root       0 -20       0      0      0 S  0.0  0.0   0:00.00 ata_sff                                                               
   20 root      20   0       0      0      0 S  0.0  0.0   0:00.00 khubd                                                                 
   21 root       0 -20       0      0      0 S  0.0  0.0   0:00.00 md                                                                    
   22 root       0 -20       0      0      0 S  0.0  0.0   0:00.00 devfreq_wq                                                            
   25 root      20   0       0      0      0 S  0.0  0.0   0:00.00 khungtaskd                                                            
   26 root      20   0       0      0      0 S  0.0  0.0   0:00.70 kswapd0                                                               
   27 root      25   5       0      0      0 S  0.0  0.0   0:00.00 ksmd                                                                  
   28 root      39  19       0      0      0 S  0.0  0.0   0:00.59 khugepaged                                                            
   29 root      20   0       0      0      0 S  0.0  0.0   0:00.00 fsnotify_mark                                                         
   30 root      20   0       0      0      0 S  0.0  0.0   0:00.00 ecryptfs-kthrea                                                       
   31 root       0 -20       0      0      0 S  0.0  0.0   0:00.00 crypto                                                                
   43 root       0 -20       0      0      0 S  0.0  0.0   0:00.00 kthrotld                                                              
   66 root       0 -20       0      0      0 S  0.0  0.0   0:00.00 deferwq                                                               
   67 root       0 -20       0      0      0 S  0.0  0.0   0:00.00 charger_manager                                                       
  108 root      20   0       0      0      0 S  0.0  0.0   0:00.00 scsi_eh_0                                                             
  109 root      20   0       0      0      0 S  0.0  0.0   0:00.02 scsi_eh_1                                                             
  110 root       0 -20       0      0      0 S  0.0  0.0   0:00.00 firewire                                                              
  111 root       0 -20       0      0      0 S  0.0  0.0   0:00.00 firewire_ohci                                                         
ari_ronnie@gateway:~$ htop
ari_ronnie@gateway:~$
```

```
ari_ronnie@gateway:~$ free
             total       used       free     shared    buffers     cached
Mem:       1998152    1612344     385808      38728      29116     777376
-/+ buffers/cache:     805852    1192300
Swap:      2031612      16872    2014740
```

---

### Post by mastablasta on 2014-04-19
what graphics card do you have? Ubuntu is modern operating system aimed at latest mashcines. for older and slower computers using Xubuntu or Lubuntu works best. Ofcourse Ubuntu can also be used but needs to be tweaked quite a bit. and 3D accelerated unity interface might need to be dumped.

---

### Post by Chris_Sabian on 2014-04-19
compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS480M [Mobility Radeon Xpress 200]

---

### Post by sudodus on 2014-04-19
Welcome to the Ubuntu Forums :-)

I suggest that you try some other flavour of Ubuntu with a lighter desktop environment, ***Xubuntu*** which is medium light or ***Lubuntu*** which is ultra light.

If you have a fast internet connection, I suggest that you download the corresponding iso files. You can use 32-bit as well as 64-bit versions, and I think with only 2 GB RAM, it might be better with 32 bits (others might advice differently).

-o-

If you have a slow internet connection, or you want a quick solution, you can ***install the corresponding flavours or only the desktop environments*** with the following commands from a terminal window

```
sudo apt-get install xubuntu-desktop
sudo apt-get install Lubuntu-desktop

```
```
sudo apt-get install xfce4
sudo apt-get install lxde

```
and then you can select the desktop environment at the login screen. But this method means that the system will get doublets for many tasks, and it is difficult to get a clean system (again).

---

### Post by Chris_Sabian on 2014-04-19
newbie questions:
- should i have downloaded the 64 bit? would it have made any difference?
 -Based on the specs, should i downgrade to a faster distro, Xubuntu, etc..if so, which one is preferrable (i use this laptop only for web browsing - no gaming)
- is it possible to keep Ubuntu on and run other lighter version of Linux. if so, whats the quickest way

Sorry, lot's of questions.  Recent convert from Windows, quite literally one day, but already loving Ubuntu.

---

### Post by Chris_Sabian on 2014-04-19
i think i am going to go with one...Xubuntu...downloading now.  what's these codes do?
sudo apt-get install xfce4sudo apt-get install lxde

---

### Post by sudodus on 2014-04-19
I think it makes no big difference in speed. A different desktop environment and a different choice of application programs will make a bigger difference.

I think Xubuntu might be a good choice. You can test both desktops in the same system according to the second alternative in my previous post.

---

### Post by Chris_Sabian on 2014-04-19
Thanks for your prompt replies, guys.  Appreciate it.  I am going to try to use Xubuntu.  Just curious, the tweaks to make Ubuntu faster, is it a tremendous effort? I am just trying to assess the level of difficulty.

---

### Post by sudodus on 2014-04-19
Standard Ubuntu is not very easy to tweak, instead it is made robust and for relatively new computers. The community flavours (Xubuntu etc) are easier to tweak.

---

### Post by The Cog on 2014-04-19
> **Chris_Sabian said:**
> i think i am going to go with one...Xubuntu...downloading now.  what's these codes do?
sudo apt-get install xfce4sudo apt-get install lxde

They install the other desktop GUI software. 
apt-get is the software package manager for installing and removing software. 
sudo is a command that effectively means "run the following command as administrator". 

So "sudo apt-get install xfce" says that as administrator, install the package xfce4. xfce4 is the GUI that Xubuntu uses. Similarly, lxde is the GUI that Lubuntu uses. You can install them all into Ubuntu, and have a choice of which GUI to run as you log in.

However, I would suggest that you go ahead with a complete install of Xubuntu and overwrite Ubuntu. Ubuntu will load a number of services that are of little use in the xfce4 GUI, and Xubuntu loads a number of services that are of use in xfce4 and not loaded by Ubuntu. Your best experience will be with the *buntu version for the GUI you intend to use.

Good luck with it.
I don't think you will find any easy tweaks to make it faster. They try to make it pretty-much as fast as they can before they release it. You won't find a settings slider that says "Glacial" and one end and "Ludicrous Speed" at the other end.

---

### Post by grahammechanical on 2014-04-19
This will tell you if your graphic card is capable if running Ubuntu+Unity with 3D acceleration

```
/usr/lib/nux/unity_support_test -p
```

This is what I see

> OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  3.0 Mesa 10.1.0


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes


If you do not get a Yes on every line then Ubuntu will load an open source driver called llvmpipe, which attempts to give a 3D accelerated appearance on cards that do not support Unity. Even on cards that do support Unity, llvmpipe gives a tolerable but not an optimal experience.

Regards.

---

### Post by Chris_Sabian on 2014-04-19
I got yes on all.  I did as recommended by Sudodus - installed the Xubunto-desktop (sudo apt-get install xubuntu-desktop) and then got the Xfce4.  Now when i boot, i only get the Xubuntu.  Is there anyway to switch back to Ubuntu? When i boot, it doesn't give me the option to choose between Xubuntu and ubuntu.

---

### Post by sudodus on 2014-04-19
Yes, you can click on the round symbol according to the attached picture and select session. Unity is the standard Ubuntu desktop.

---

