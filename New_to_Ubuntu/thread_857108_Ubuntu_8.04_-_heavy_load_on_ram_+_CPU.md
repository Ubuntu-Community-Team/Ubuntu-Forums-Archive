---
title: "Ubuntu 8.04 - heavy load on ram + CPU ???"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by poiiop on 2008-07-12
Hi

Installed a clean 8.04 on a 3Ghz, 2GB PC but the system is not running smoothly.

Have installed the following:
Proftpd ftp program
VMware Server
Citrix Client
Azureus incl. JAVA
SAMBA server
Visual effect is on normal
and ... I have open for 3.party software

When I start the PC, the ram used is almost immediately above 1GB - and I have not startet anything except SAMBA and Proftpd. Right now Azureus and firefox is the only programs started, and the free -m show this after a while:

total__used___free___shared___buffers__cached
2025___1967___57_____0________98_______1388

A top show this:

top - 11:25:39 up  1:11,  3 users,  load average: 0.28, 0.43, 0.52
Tasks: 123 total,   2 running, 121 sleeping,   0 stopped,   0 zombie
Cpu(s): 45.0%us,  4.0%sy,  0.0%ni, 50.0%id,  0.7%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   2074228k total,  2016820k used,    57408k free,   115900k buffers
Swap:  6072528k total,        0k used,  6072528k free,  1405296k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND              
 5203 root      20   0  283m  64m 9116 S 19.6  3.2   4:28.89 Xorg                 
 5864 axl       20   0  206m  78m  26m S 18.6  3.9   2:47.79 firefox              
 5783 axl       20   0 1238m  88m  23m S  8.7  4.4   3:41.58 java                 
 5716 axl       20   0 24324  16m 6868 S  1.3  0.8   0:21.68 compiz.real          
 6119 axl       20   0 66276  19m  10m R  0.7  0.9   0:03.36 gnome-terminal       
    1 root      20   0  2844 1688  544 S  0.0  0.1   0:01.26 init                 
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd             
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0          
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0          
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0           
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 events/0             
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper              
   42 root      15  -5     0    0    0 S  0.0  0.0   0:00.26 kblockd/0            
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid               
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify         
  112 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod              
  146 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush              
  147 root      20   0     0    0    0 S  0.0  0.0   0:00.16 pdflush              


All to often the CPU goes near 100% and my CPU fan is speeding up to max RPM. The CPU usage is Xorg, Gnome-system-mo, Firefox etc. 

Is is wrong to turn on the 3. party software ?? Any hints to reduce the heavy load ??

---

### Post by ibuclaw on 2008-07-12
> **poiiop said:**
>   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND              
 5203 root      20   0  283m  64m 9116 S 19.6  3.2   4:28.89 Xorg                 
 5864 axl       20   0  206m  78m  26m S 18.6  3.9   2:47.79 firefox              
** 5783 axl       20   0 1238m  88m  23m S  8.7  4.4   3:41.58 java **                
 5716 axl       20   0 24324  16m 6868 S  1.3  0.8   0:21.68 compiz.real          
 6119 axl       20   0 66276  19m  10m R  0.7  0.9   0:03.36 gnome-terminal       
    1 root      20   0  2844 1688  544 S  0.0  0.1   0:01.26


Looks like it is almost certainly azureus that is giving the most burden on the system.

How to tweak it, I'm not too sure.

But you'll have to keep disk I/O to a minimum, and maybe try setting your swappiness to a low value.

Regards
Iain

---

### Post by mcduck on 2008-07-12
First, based on the free -m output your are using 1967MB of memory, out of which 98MB is buffers and 1388MB is cached data. So your system and programs are actually using only 481MB of memory.

Linux/Unix uses all available RAM. The part that is not needed by system or running programs is used as disc cache to give more performance. RAM should be used, you don't get any benefits from having unused memory. If some program needs more memory some cached data is just dropped to free more RAM.

When you use the "free -m" to check the memory usage you should read the "+/- buffers & cache"-line. That's what's telling you how much RAM your system and programs are really using.

What comes to CPU use, Firefox can use a lot of CPU power if you are surfing on web sites that use Flash. That's normal, its just the way Flash is. Java is another CPU hog, that's why I'd recommend avoiding Azureus and other Java apps as long as there is better alternatives around.

Running any virtual machines _will_ definitely take a lot of memory and CPU power. So if you start WMware Server you should expect hight memory & CPU usage.

Now, whay do you mean by tunrning on 3rd party software? Enabling the 3rd party software repository? Only thing that does is that it allows you to install 3rd party software from the repositories if you want. The actual change enabling that is just adding a line or two of text in a text file that describes internet adresses where the package manager can install software. Enabling it makes no difference performance-wise. What you install from there is a different case, of course.

Based on the software you are using I don't see anything special in your CPU & memory usage.

edit: fixed a nasty (although quite amusing) little typo..

---

### Post by philinux on 2008-07-12
If you try Deluge instead of Azureus you'll notice that it's much lighter on resources.

---

### Post by squee on 2008-07-12
Or use Transmission. It really good and very light in comparison to Azureus.

---

### Post by poiiop on 2008-07-12
Thx for all your answers.

I wasn't aware of the free ram cached part - thx mcduck - that explains alot. And yes, it was the 3.part repository I was referring to.

I will skip my JAVA for now ..

---

### Post by hyper_ch on 2008-07-12
if you want a light yet powerful torrent client use rtorrent in conjunction with screen

---

