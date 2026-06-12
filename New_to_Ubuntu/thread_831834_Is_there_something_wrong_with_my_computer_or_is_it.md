---
title: "Is there something wrong with my computer? or is it ubuntu?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Cebonet on 2008-06-17
I just wanna ask one thing: " can ubuntu make a computer unuseable?( dont know the word really exist) " 

2 months ago i' ve installed ubuntu on my medion 5400 laptop. It worked fine, that's what I thought it did. I realized that the computer was getting warm, very fast in ubuntu, but not in windows( had dualboot). I did'n take it serious, thought one day the computer shutted down suddenly, and i could smell "something burned". The computer started again when I hited the start button, but the usb-ports, bluetooth and the speaker were not working. So I've send it to medion, and they repaired it.

When I had it on my hands, I installed the ubuntu again with the risk. When the installation was completed, I could hear the harddisk making noise(didn't do it before), I' ve got scared and uninstalled ubuntu. now the hard drive makes noise in windows too.

Now I don't know what to do, should I take the risk and install ubuntu, maybe nothing will happen:). 

Does ubuntu have the power to destroy my pc. What I am thinking is, maybe the computer did't burn becouse I was using ubuntu, maybe it would happen in windows too, I'm not sure. 

what I wanna know, do you think ubuntu is the quilty one?, HOW CAN IT BE POSSIBLE). 

any idea?

(sorry my bad spellin)

---

### Post by sharks on 2008-06-17
I think it may be a hardware problem. try verifying your ubuntu cd. boot ubuntu cd and choose option to CHECK CD FOR DEFECTS> I think that Ubuntu will not destroy computer.

---

### Post by eldragon on 2008-06-17
you definately had heat issues and thats what broke your computer.

evidently the same heat that broke your (probably) motherboard, knacked your hdd and it will eventually die.

i would definately send the computer back for repairs if the hdd is dying and its still under warranty.

as of why the computer heated up...might be related to a fan failure, or maybe ubuntu doesnt play well with your laptop's power management features and made it overheat. i dont know much about how to debug this problem (Which whould be a good idea in order to prevent this from happening again in the future), but i bet someone in this forums, or even launchpad could help out. have you considered filing a bug on launchpad concerning your problem?

---

### Post by fatality_uk on 2008-06-17
The hardware does seem to be at fault. As suggested, take the PC back to the people you bought it from.

---

### Post by Ghliofris on 2008-06-17
It does sound like hardware failure. The question is what hardware. You got it repaired, what did they replace and or fix? It sounds to me that the cooling fan took a dump. I know that when this happens it can cause other problems down the road, mainly with the CPU. If a CPU overheats, it can "take out" the motherboard too. This can cause other hardware failures.

My advise is to take it back to where you got it repaired the first time and have them run diags on it. This will tax the system and give error codes on failed or failing hardware. A read/write diag to the harddrive should show that it needs to be replaced.

---

### Post by alienexplorers on 2008-06-17
Since installing first Ubuntu 6.06 and every version there after I have blown 4 hard drives.  When running windows I never had a problem.  It seems in Ubuntu that my disk never stops being accessed.  If anyone has a answer to this I'd like to hear from them before the disk I am using blows.

BTW- I have tried Maxtor, Seagate, and Western Digital Drives.  In my system now is a 40GB Maxtor drive.

---

### Post by Ghliofris on 2008-06-17
> **alienexplorers said:**
> Since installing first Ubuntu 6.06 and every version there after I have blown 4 hard drives.  When running windows I never had a problem.  It seems in Ubuntu that my disk never stops being accessed.  If anyone has a answer to this I'd like to hear from them before the disk I am using blows.

BTW- I have tried Maxtor, Seagate, and Western Digital Drives.  In my system now is a 40GB Maxtor drive.

Have you run system monitor to see what is going on? Could be a run-away proggy. Add all the memory to it and sort by each one. See what is using the most memory. Did you create the partitions on install or did you let it do it?

---

### Post by alienexplorers on 2008-06-17
I created the partitions.  As for a runaway program, when I look in system monitor most if not all programs show as sleeping, yet the drive light is blinking on and off.  At first I used the motherboards IDE controller.  Finally thought that the IDE controller was bad and so I bought a new one.  Still having the problems.
Running TOP in terminal shows this:
> terminator@terminator-desktop:~$ top

top - 10:56:41 up  6:13,  2 users,  load average: 0.50, 0.55, 0.46
Tasks: 102 total,   2 running, 100 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.3%us,  1.3%sy,  0.0%ni, 94.4%id,  0.0%wa,  0.3%hi,  0.7%si,  0.0%st
Mem:    385532k total,   376448k used,     9084k free,     8724k buffers
Swap:   987988k total,    42300k used,   945688k free,   162052k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5503 root      20   0 65808  27m 8624 S  2.3  7.4  15:50.76 Xorg               
 6031 terminat  20   0 56752  26m 8784 S  1.3  6.9   5:19.66 compiz.real        
11643 terminat  20   0  2208 1072  824 R  1.3  0.3   0:00.42 top                
 5883 terminat  20   0 42596  18m  12m S  0.7  5.0   2:40.91 gnome-panel        
 5944 terminat  20   0 20572 4596 3412 S  0.7  1.2   0:00.44 gnome-volume-ma    
11621 terminat  20   0 63784  17m  10m S  0.7  4.8   0:02.54 gnome-terminal     
 5839 terminat  20   0 43144  13m 8624 S  0.3  3.6   0:16.71 gnome-settings-    
    1 root      20   0  2752 1668  524 S  0.0  0.4   0:04.00 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.44 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 khelper            
   39 root      15  -5     0    0    0 S  0.0  0.0   0:01.22 kblockd/0          
   42 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   43 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify 

---

### Post by Ghliofris on 2008-06-18
hmmm Swap file is large enough. Physical RAM is enough. OK, dumb question, please don't take offense to it, are you running the 386 version?

---

