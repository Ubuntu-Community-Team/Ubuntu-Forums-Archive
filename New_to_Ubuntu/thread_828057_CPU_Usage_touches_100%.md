---
title: "CPU Usage touches 100%"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by jaipraveen on 2008-06-13
I use Ubuntu 7.10- the Gutsy Gibbon.It takes hell  of a time to run applications(even switching between applications)..Damn slow.

Recently I figured out that my CPU usage touched 100% sometimes and keep on doing so periodically.I couldn't find a solution for this.I checked my swap space.This is the output of swapon -s


Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       497972  0       -1


Somebody , pls help me with this prob

Thanks,
Jai Praveen

---

### Post by aktiwers on 2008-06-13
I would guess it is the program called Tracker that does this, in this case we need to stop it from running on startup.

But could you go to Terminal (applications=>Accessories=> Terminal)
And type in:
```
top
```Then copy/paste the output here. Then we should be able to see what is eating your CPU.

And Welcome to Ubuntu

---

### Post by aktiwers on 2008-06-13
In any case you could always try go to System=>Preferences=>Sessions 

And disable Tracker. It has cost me these problems in the past. Look at my screenshot below:

---

### Post by jaipraveen on 2008-06-13
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 4632 root      15   0 58920  17m 6780 S 18.9  2.3   4:29.92 Xorg                                                            
 4860 jai       15   0  129m  40m  25m S 14.4  5.3   4:17.94 amarokapp                                                       
 3697 root      18   0  4608 1888  616 R  5.8  0.2   2:41.29 mount.ntfs                                                      
 4841 jai       15   0 80896  22m  12m S  5.8  2.9   0:03.62 gnome-terminal                                                  
 5172 jai       16   0 29752  17m  12m S  3.4  2.3   1:05.47 gnome-system-mo                                                 
 4818 jai       15   0 31632  16m  11m S  1.3  2.2   0:06.78 gnome-panel                                                     
 4866 jai       15   0 16516 2636 1748 S  0.9  0.3   0:05.21 gnome-screensav                                                 
 5288 jai       15   0  2364 1152  876 R  0.4  0.1   0:00.07 top                                                             
    1 root      15   0  2952 1852  532 S  0.0  0.2   0:01.72 init                                                            
    2 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                        
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                     
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                     
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                      
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.11 events/0                                                        
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper                                                         
   26 root      17  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                       
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                          
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                    
  100 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                         
  119 root      16   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                         
  120 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                         
  121 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                         
  172 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                           
 1970 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                   
 1971 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                           
 1986 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 ata/0                                                           
 1987 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                         
 2001 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                       
 2002 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 scsi_eh_1                                                       
 2301 root      10  -5     0    0    0 S  0.0  0.0   0:00.07 kjournald                                                       
 2506 root      13  -4  3040 1392  408 S  0.0  0.2   0:00.60 udevd                                                           
 3373 root      18  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused

---

### Post by lswest on 2008-06-13
did you copy this when the CPU was at 100%?  and also, what're the specs on the CPU?

---

### Post by aktiwers on 2008-06-13
Okay it seams like your CPU is not a 100% right now, making it hard to identify what app causes this.
But again I would think it is the tracker app, which uses lots of CPU when it indexes your files so you can search them.

I personally never use this and has disabled it (like shown in my 2. post).

Try do the same and restart X (CTRL+ALT+Backspace) or simply logout and in again.
I think this would fix your problem :)

---

### Post by wPwLUi3N on 2008-06-13
Your %cpu doesn't seem to touch 100% (50.9)%, are you sure this data when cpu is 100%

Is this problem from start in a fresh install?

---

### Post by jimbean on 2008-07-06
had the same problem 100 percent usage
went into bios and checked turbo settings
now am down to 35 percent most of the time
intel celeron 2.4
64 mb nvidia card
256 mb mem ddr 266
300 gig hd seagate
award bios
beware :: use at own discretion can lockup system
cant be of much help beyond that

---

### Post by rybu on 2008-07-07
I'm having a similar problem right now.  It's ksoftirqd/1 that's hogging the processor time.  

When I use a cable ethernet connection it doesn't happen, but when I'm using wireless heavily it seems to happen every once and a while.  Sometimes it temporarily locks-up GNOME.

It's unresponsive to kill commands.

---

### Post by ibuclaw on 2008-07-07
There is a known bug in the gnome-system-monitor that causes itself to take up an abnormally large amount of CPU on Xorg.
I believe this is generally single core processors that suffer the most burden.
Read here: [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

So just ignore what it says for the moment and use top to identify your system processes.

And try not to relate the usage of the CPU to what the MS Task Manager displays.

100% = the CPU is being powered at 100% of it's volt usage. It does not in anyway imply that anything is slowing down your system.
Linux has exceptional resource handling to ensure that it doesn't happen ;)

Regards
Iain

---

