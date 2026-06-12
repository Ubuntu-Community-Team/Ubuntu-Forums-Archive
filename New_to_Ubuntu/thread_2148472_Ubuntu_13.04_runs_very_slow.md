---
title: "Ubuntu 13.04 runs very slow"
date: 2013-05-25
forum: New to Ubuntu
---

### Post by josef123 on 2013-05-25
Hello everyone,


I installed for the first time Ubuntu 13.04 (64X UNITY) on my computer, and deleted my old windows. I Was sure I was going to improve my computer performance, but I found that Ubuntu is running very slow. Every simple task takes a lot of time and the loading time takes forever. It's funny because my system now have a slower response time comperes to the response time of my old windows.

the hardware is old, but relatively fine:


Processor: Intel ® Core ™ 2 Duo CPU E6750@2.66GHz × 2


Memory: 4GB (Samsung 1GB PC2 6400 240pin PC2-6400 DDR2 800 X4) 


Graphics Processor: Geforce 8500 GT 256MB (DRIVER: Gallium 0.4 on NV86)



What do you think the problem is and how can I fix it?


(Please note that the Linux experience is new to me).

---

### Post by 2F4U on 2013-05-25
Did you open task manager (or something like top or htop, if you prefer this) and check if some application is causing a high CPU utilization? Did you check whether additional drivers, in particular for the graphics card are available?

---

### Post by grahammechanical on 2013-05-25
You have 4 x times the RAM as I do but I have a similar CPU, actually lower specification, Intel Core 2 Duo 6600 @ 2.40GHZ. I get a better response than you do. I would suggest that the problem lies with the video card and the 256MB memory on it. You are also using the Nouveau open source driver. That is what Gallium means. The NV86 is the Nvidia code for the Geforce 8500 GT.

I have the GT220 1GB  Memory and I get good response with Nouveau but you might need the Nvidia driver. 

I have just thought of something else. You might be running Gallium llvmpipe which is the open source fall back driver when no video driver is activated. That I know gives very slow performance. My system has dropped into it at least once when something broke the desktop. So, go to System Settings>Software & Updates>Additional Drivers tab and experiment with video drivers, including the full blown Nouveau.

P.S. You may find that some of the Nvidia drivers do not work well. If the system loads to a desktop with just wallpaper and no top panel or launcher, then right click the desktop and select Change Desktop Background and that will open System Settings and from there you can get to Software & Updates again and try another video driver.

Regards.

---

### Post by marlow59 on 2013-05-25
reboot the computer, and just as it's done booting press ctrl-alt-t (at the same time) or open the launcher (super or "windows" button) then type in "Terminal". Once you're there run ```
 top 
``` or ```
 htop 
``` command and past the output here please. (note that you will need to press the q key or ctrl-c to stop the command). Hope it helps :)

---

### Post by rvergara on 2013-05-25
Hi there.

I just installed 13.04 on a Netbook Samsung N100S (2GB in RAM).

The desktop is painfully slow, I checked top CPU processes using top and it is just consuming less than 20% being compiz the largest CPU consumer with around 10%. Is it possible to use Unity 2D with 13.04 or gnome classic just to check if compiz in the one to blame?

Thanks

---

### Post by 3rdalbum on 2013-05-25
Try grahammechanical's advice FIRST.

Ubuntu 13.04 only really runs acceptably with full 3D acceleration. Your graphics card needs the official Nvidia driver to get the full acceleration, and the Software & Updates program can install that driver for you. Afterwards, and after a reboot, your desktop will be speedy.

rvergara: You are asking a different question, please use a different thread. Briefly, no there is no Unity 2D, but yes you can install Gnome Panel from the Software Center and select Gnome Classic at the login screen.

---

### Post by josef123 on 2013-05-25
thank you all for the quick responses!

this is the utilization:

top - 19:42:07 up 0 min,  2 users,  load average: 0.86, 0.26, 0.09
Tasks: 172 total,   1 running, 171 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.8 us,  3.0 sy,  0.0 ni, 91.0 id,  5.2 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   3978396 total,   613048 used,  3365348 free,    67016 buffers
KiB Swap:  4121596 total,        0 used,  4121596 free,   230784 cached


  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND           
 1090 root      20   0  195m  50m  16m S   6.0  1.3   0:01.70 Xorg              
 1983 joe       20   0  596m  19m  12m S   1.0  0.5   0:00.28 gnome-terminal    
 1642 joe       20   0 1033m  76m  35m S   0.3  2.0   0:01.56 compiz            
    1 root      20   0 26920 2780 1424 S   0.0  0.1   0:00.72 init              
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kthreadd          
    3 root      20   0     0    0    0 S   0.0  0.0   0:00.04 ksoftirqd/0       
    4 root      20   0     0    0    0 S   0.0  0.0   0:00.01 kworker/0:0       
    5 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kworker/0:0H      
    6 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kworker/u:0       
    7 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kworker/u:0H      
    8 root      rt   0     0    0    0 S   0.0  0.0   0:00.03 migration/0       
    9 root      20   0     0    0    0 S   0.0  0.0   0:00.00 rcu_bh            
   10 root      20   0     0    0    0 S   0.0  0.0   0:00.10 rcu_sched         
   11 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 watchdog/0        
   12 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 watchdog/1        
   13 root      20   0     0    0    0 S   0.0  0.0   0:00.02 ksoftirqd/1       
   14 root      rt   0     0    0    0 S   0.0  0.0   0:00.02 migration/1

---

### Post by lethall1 on 2013-05-25
```
[FONT=Ubuntu Mono]sudo hdparm -Tt /dev/sda[/FONT]
```
paste output here, please

---

### Post by josef123 on 2013-05-25
Timing cached reads:   7502 MB in  2.00 seconds = 3753.53 MB/sec
 Timing buffered disk reads: 226 MB in  3.01 seconds =  75.03 MB/sec

---

### Post by lethall1 on 2013-05-25
Nice drive speed, if it is where you ubuntu installed (sorry, forgot to ask disk lable)
Your CPU and RAM loading is in normal, HDD speed in normal (again if it is it) 
Try to play with graphical card driver. 
Do you have more than 1 HDD installed in PC? If yes, try this command for each of them.
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo hdparm -Tt /dev/sdX[/FONT][/COLOR]
``` X-letter that should be changed

i have netbook, thak works just fine with this speed:
>  Timing cached reads:   1414 MB in  2.00 seconds = 706.91 MB/sec Timing buffered disk reads: 226 MB in  3.01 seconds =  75.11 MB/sec


---

### Post by josef123 on 2013-05-25
i only have one HDD. it is probably as you said the problem is with the drivers.

---

### Post by lethall1 on 2013-05-25
Did you install proprietary driver? Menu- setting - drivers (or proprietary driver).

---

