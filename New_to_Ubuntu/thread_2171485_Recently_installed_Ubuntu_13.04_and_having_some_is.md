---
title: "Recently installed Ubuntu 13.04 and having some issues."
date: 2013-08-31
forum: New to Ubuntu
---

### Post by nothingwillgowrong on 2013-08-31
[NEW THREAD ABOUT WIRELESS ISSUES]("http://ubuntuforums.org/showthread.php?t=2171772")

Recently built a new PC. Installed Ubuntu 13.04. 

It is. Slow. As. Molasses.

Seriously, I tried installing Steam and it's slow as a snail, I tried running Dota 2 and it's slow. 

Literally opening browsers is slow. EVERYTHING IS SUPER SLOW.

Normally this wouldn't surprise me but here are my computer's specs....

[SIZE=2]RAM: [/SIZE]**[SIZE=2]Kingston HyperX Black Series 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Desktop Memory Model KHX16C9B1BK2/8[/SIZE]**

[SIZE=2]Hard Drive: 
[/SIZE]**[SIZE=2]Western Digital WD Blue WD10EZEX 1TB 7200 RPM 64MB Cache SATA 6.0Gb/s 3.5" Internal Hard Drive - OEM[/SIZE]**

[SIZE=2]
CPU:
[/SIZE]**[SIZE=2]AMD A10-6800K Richland 4.1GHz (4.4GHz Turbo) Socket FM2 100W Quad-Core Desktop Processor - Black Edition AMD Radeon HD 8670D[/SIZE]**

[SIZE=2]Power Supply:
[/SIZE]**[SIZE=2]COOLER MASTER eXtreme Power Plus RS-550-PCAR-E3 550W ATX12V V2.3 SLI Ready CrossFire Ready Power Supply[/SIZE]**

[SIZE=2]
Mother Board:
[/SIZE]**[SIZE=2]MSI FM2-A75MA-E35 FM2 AMD A75 (Hudson D3) HDMI SATA 6Gb/s USB 3.0 Micro ATX AMD Motherboard[/SIZE]**



As far as I can tell it should be running much faster than this... even my download rate which on this network is ordinarily close to 2.0mb/s is never reaching more than 35kb/s. . . Everything is just completely bogged down and I'm out of ideas.

Any solutions much appreciated. I was really hoping to get Dota 2 running on this machine but it can barely even start let alone render or anything. 

Will post additional information on request.

Thanks in advance.

---

### Post by ibjsb4 on 2013-08-31
Open a terminal and enter:

```
top
```

Any clues?

---

### Post by nothingwillgowrong on 2013-08-31
```
colin@Paul:~$ top

top - 00:04:10 up 4 min,  2 users,  load average: 1.32, 0.98, 0.44
Tasks: 196 total,   3 running, 193 sleeping,   0 stopped,   0 zombie
%Cpu(s): 16.9 us,  1.3 sy,  0.0 ni, 81.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   7288548 total,  1355920 used,  5932628 free,    41056 buffers
KiB Swap:  7551996 total,        0 used,  7551996 free,   468808 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND           
 1649 colin     20   0 1638m 306m  36m R  64.5  4.3   4:06.95 compiz            
 1105 root      20   0  321m 118m  24m R   9.0  1.7   0:50.95 Xorg              
 2341 colin     20   0  592m  18m  12m S   2.0  0.3   0:00.23 gnome-terminal    
  252 root      20   0     0    0    0 S   0.3  0.0   0:00.15 kworker/0:1       
 1978 colin     20   0  783m 128m  38m S   0.3  1.8   0:15.98 firefox           
 2397 colin     20   0 24828 1608 1120 R   0.3  0.0   0:00.01 top               
    1 root      20   0 26808 2688 1436 S   0.0  0.0   0:00.85 init              
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kthreadd          
    3 root      20   0     0    0    0 S   0.0  0.0   0:00.03 ksoftirqd/0       
    4 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kworker/0:0       
    5 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kworker/0:0H      
    6 root      20   0     0    0    0 S   0.0  0.0   0:00.93 kworker/u:0       
    7 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kworker/u:0H      
    8 root      rt   0     0    0    0 S   0.0  0.0   0:00.02 migration/0       
    9 root      20   0     0    0    0 S   0.0  0.0   0:00.00 rcu_bh            
   10 root      20   0     0    0    0 S   0.0  0.0   0:00.14 rcu_sched         
   11 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 watchdog/0        

```

Noticed the CPU is fluctuating between 5 and 111% on that first process. 

Is that a sign of overheating or something? Bad heatsink?

EDIT: Worth noting, despite the fact that my browser is able to load, any download done through Steam is completely frozen.

---

### Post by 3rdalbum on 2013-08-31
Did you install the AMD/ATI graphics driver?

(check the Software Sources program)

---

### Post by nothingwillgowrong on 2013-08-31
> **3rdalbum said:**
> Did you install the AMD/ATI graphics driver?

(check the Software Sources program)

No I did not. I suspected that would be important but honestly I have no idea how, the disc it came with is Windows not Ubuntu and I have no idea how or where to look to install the AMD/ATI drivers. (I didn't see anything in USC but who knows)

Any advice on how?

---

### Post by su:bhatta on 2013-08-31
If you are using Ubuntu then search for 'Software and Updates' from the Dash, In the last tab of the "softwares and Updates' you will see Additional Drivers, use radio button to choose fglrx or fglrx-updates, wait for the 'Applying Changes' to finish then reboot. 

Here is the help page for ATI/AMD drivers : [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by newb85 on 2013-08-31
+1 to installing the graphics drivers.

Meanwhile, I still have a hard time believing Compiz would take 64% of your quad-core processor (unless you've customized Compiz ridiculously).  Could you run
```
lscpu
```
just to make sure everything checks out there?

---

### Post by eternal243 on 2013-08-31
to me it seems like compiz is causing a memory leak or something, what happens if you disable compiz? if that solves the problem, then you could try to uninstall it and then reinstall to see if you still get the same problem.

---

### Post by ibjsb4 on 2013-08-31
> **3rdalbum said:**
> Did you install the AMD/ATI graphics driver?
(check the Software Sources program)

Sounds like the fix.

> **eternal243 said:**
> to me it seems like compiz is causing a memory leak or something, what happens if you disable compiz? if that solves the problem, then you could try to uninstall it and then reinstall to see if you still get the same problem.

I don't think its compiz, but you could install and run another window manager just to find out.  You could install gnome-classic --no-effects and choose to run it at boot (login) by clicking on the icon in the login window.  This will get you off compiz and will use metacity instead.

To install classic:
```
sudo apt-get install gnome-session-fallback
```

---

### Post by nothingwillgowrong on 2013-08-31
Here is the results of lspcu:

```
[sudo] password for colin: 
sudo: update: command not found
colin@Paul:~$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            21
Model:                 19
Stepping:              1
CPU MHz:               2000.000
BogoMIPS:              8200.56
Virtualization:        AMD-V
L1d cache:             16K
L1i cache:             64K
L2 cache:              2048K
NUMA node0 CPU(s):     0-3
colin@Paul:~$ 

```

```
colin@Paul:~$ sudo apt-get install gnome-session-fallback
[sudo] password for colin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-session-fallback is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gnome-session-fallback' has no installation candidate
colin@Paul:~$ 
```


Also something I'm noticing. If I reset using the menu my internet is disabled when I restart. If I do it with the reset button on the chassis then it isn't.

Also fglrx showed up in the drivers menu thing initially and I hit the buttons to switch to it, did a restart and now nothing shows up and whenever I've tried to download it it hasn't been working.

However... 

```
colin@Paul:~$ fglrxinfo
fglrxinfo: command not found
colin@Paul:~$ fglrx
fglrx: command not found
colin@Paul:~$ sudo update fglrx
[sudo] password for colin: 
sudo: update: command not found
colin@Paul:~$ 

```

I've been trying to download and install drivers somehow but it's been painfully slow and hasn't really been working (so far)

The first one I tried downloaded fine but it finished at 4.8 mb instead of like 78 mb it was listed as and it won't run or open (I'm assuming the download somehow got cutoff, I'm installing another one as we speak and yes I deleted the one that failed to download)

Any ideas? :/

---

### Post by Jonathan Precise on 2013-08-31
nothingwillgowrong, _**YIKES!!!!!!**_

Go to Software and Updates. Change the server to:

> Main Server

or:

> Server for United states

If still no, then on the Third-Party tab, disable the gnome 3 PPA

If nothing has changed then go to a terminal and type in:

```
sudo apt-get install lxde
```

That should install LXDE (Even lighter than GNOME (No effects). Uses openbox.). On the login window, click the ubuntu logo. Select "LXDE''.

---

### Post by ibjsb4 on 2013-08-31
Have you updated your system since you installed it?

---

### Post by nothingwillgowrong on 2013-08-31
> **ibjsb4 said:**
> Have you updated your system since you installed it?

Not as far as I know. This is actually the second time I've installed Ubuntu, I did a complete system wipe and reinstalled over it once already (before starting this thread) because after I did a system update my wi-fi was disabled and I couldn't get internet or anything.

I got the fglrx driver working however, 

```
colin@Paul:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.2, 128 bits)
OpenGL version string: 1.4 (2.1 Mesa 9.1.3)

```



IS this the right thing I should be using?

Also, the machine is still running incredibly slow despite this. That compiz process is still taking up a ton of power when I use "top" in the terminal (it fluctuates between 5ish% and over 100% averaging around 50%)

> **Jonathan Precise said:**
> If nothing has changed then go to a terminal and type in:
```
sudo apt-get install lxde
```
That should install LXDE (Even lighter than GNOME (No effects). Uses  openbox.). On the login window, click the ubuntu logo. Select "LXDE''.                 

Doing this as we speak; stay tuned.

EDIT: After the restart I now have a giant **"AMD UNSUPPORTED HARDWARE"** notification tag thing stuck in the bottom right corner of my screen that will not go away...

EDIT2: Compiz doesn't seem to be spiking out of control anymore, however the computer is still running really slowly and my download rate never peaks past 55kb/s despite easily reaching much higher on an adjacent laptop using the same network. 

[SPEED TEST FOR ADJACENT LAPTOP]("http://www.speedtest.net/my-result/2937024577")

> _Overall Summary of Current problems_

-Slow running speed.
-Giant "AMD UNSUPPORTED HARDWARE" thing on the bottom right of the screen.
-Very very slow download rate. (Keep in mind I have a nearby device on the same network with less specs that's got a significantly faster download rate at the moment.)

NOTE: Graphics still may be an issue, I haven't downloaded any games to test yet since that would take several hours given its current download speed.

---

### Post by nothingwillgowrong on 2013-09-01
UPDATE: 

[Speed Test results for the computer.]("http://www.speedtest.net/my-result/2937170325")

Sorry for double post, thought this was important.

---

### Post by Impavidus on 2013-09-01
Are you on wifi or on a wired connection? There may be a problem with your wifi driver. Using a wired connection may be a (temporary) fix to download the drivers, although it shouldn't take too long on the connection you have right now. The general slowness and the slow network may not be related. Maybe you wish to start a separate thread about your slow network on [the networking subforum]("http://ubuntuforums.org/forumdisplay.php?f=336"), adding a link to this thread.

---

### Post by nothingwillgowrong on 2013-09-01
> **Impavidus said:**
> Are you on wifi or on a wired connection? There may be a problem with your wifi driver. Using a wired connection may be a (temporary) fix to download the drivers, although it shouldn't take too long on the connection you have right now. The general slowness and the slow network may not be related. Maybe you wish to start a separate thread about your slow network on [the networking subforum]("http://ubuntuforums.org/forumdisplay.php?f=336"), adding a link to this thread.

I'm thinking it's an issue with wifi drivers, since yes I am on a wireless connection (nor do I have access to a wired one at the moment). 

Normally I would blame my network but I have several devices including two laptops of much lower specs right beside me on the exact same network that have absolutely no issue downloading anything at much higher speeds. Temporarily emoving all other devices from the network has not improved speed whatsoever.

I'll make that thread in the other sub forum, and see what happens from there.

For now; if anyone else has suggestions/requires information that may help improve the speed of this thing or remove that awful "AMD UNSUPPORTED HARDWARE" thing stuck on the bottom of my screen they are welcome to suggest it.

The New Thread about Wireless issues is [HERE]("http://ubuntuforums.org/showthread.php?t=2171772&p=12776182#post12776182") for anyone interested.

---

### Post by nothingwillgowrong on 2013-09-01
Hi sorry for the double post. I'd just like to point out my issues are now solved beyond the wireless and that **this thread can be closed.** If you desire to continue helping me with my wireless troubles please visit my new thread! Cheers.

---

### Post by Jonathan Precise on 2013-09-01
Please mark this as solved by going to thread tools.
Also, please provide a link to the new thread.

---

### Post by nothingwillgowrong on 2013-09-01
New thread is [HERE.]("http://ubuntuforums.org/showthread.php?t=2171772")

thread now marked as solved.

---

