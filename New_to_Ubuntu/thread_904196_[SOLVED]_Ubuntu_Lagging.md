---
title: "[SOLVED] Ubuntu Lagging"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by BluePlum on 2008-08-29
Having a weird problem, For some reason, my ubuntu has started to " lag " every 30 seconds or less, it's been freezing a bit, kinda like what lag is like in a game, jumpy. It only lasts for 3 seconds but when it happens this much, it's horrible, It seems to stop tho when the laptop has been on for a while. So does anyone know how to fix this?

Thank you all who help!

---

### Post by nicedude on 2008-08-29
You should use top command to see what is taking up system resources and causing the slowdowns.

try running top and post the results here so everyone can see what might be causing this, the command to type in the terminal is just "top" without quotes you may need to watch the output for a minute to see the culprit.


Hope this helps

---

### Post by BluePlum on 2008-08-29
Thanks for reply, What exactly do you want me to paste? because the list of programs keeps changing.

---

### Post by Crafty Kisses on 2008-08-29
Just copy and paste what's currently running.

---

### Post by BluePlum on 2008-08-29
assasin@Invisible-Assasin:~$ top

top - 03:44:27 up  2:10,  2 users,  load average: 0.36, 0.37, 0.29
Tasks: 130 total,   3 running, 127 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.3%us,  0.7%sy,  0.3%ni, 89.8%id,  0.0%wa,  0.0%hi,  3.0%si,  0.0%st
Mem:    515312k total,   509392k used,     5920k free,     3352k buffers
Swap:  1510068k total,    44400k used,  1465668k free,   235200k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5538 root      20   0  129m  42m  10m R  7.3  8.4   8:20.50 Xorg               
 7682 assasin   20   0 21676  11m 6564 S  3.3  2.3   3:00.86 kiba-dock          
10650 assasin   20   0  137m  45m  19m R  2.0  9.1   0:09.14 firefox            
 5860 assasin   20   0  103m  39m  16m S  1.7  7.9   3:18.59 deluge             
 4752 root      15  -5     0    0    0 S  0.7  0.0   0:17.38 kondemand/0        
 5342 root      20   0  3352 1176  988 S  0.7  0.2   0:01.12 hald-runner        
 5835 assasin   20   0 77928  26m  12m S  0.7  5.3   0:03.53 nautilus           
 5994 assasin   20   0 21280 8912 7508 S  0.7  1.7   0:21.60 geyes_applet2      
    1 root      20   0  2844 1688  544 S  0.0  0.3   0:01.44 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.26 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.30 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid

---

### Post by Crafty Kisses on 2008-08-29
When does it lag the most, like just whenever or when you have a certain program open?

---

### Post by BluePlum on 2008-08-29
Just whenever, i have noticed tho in this session, when i leave it for a bit ( serveral minutes ) and come back, it will do this lag thing.

---

### Post by Crafty Kisses on 2008-08-29
What are your system specs?

---

### Post by TenPlus1 on 2008-08-29
Try turning off the Tracker service/session as this may help...

---

### Post by BluePlum on 2008-08-29
Ubuntu has been working fine for a year and a half, and my specs are.... ( get ready, they'll blow your mind! ) 

GPU - Ati radeon 900 
CPU - 1.4ghz
RAM - 512 mb
HD - 40gb

---

### Post by Crafty Kisses on 2008-08-29
> **BluePlum said:**
> Ubuntu has been working fine for a year and a half, and my specs are.... ( get ready, they'll blow your mind! ) 

GPU - Ati radeon 900 
CPU - 1.4ghz
RAM - 512 mb
HD - 40gb

Yeah those are older specs, instead of FireFox try to run SwiftFox and what not also if you have desktop effects on, turn them off.

---

### Post by BluePlum on 2008-08-29
No destop effects on... And it runs firefox fine :P, I't has run ubuntu fine, something has gone wrong and now it's lagging, i don't think it's specs...

---

### Post by Crafty Kisses on 2008-08-29
Have you changed or done anything before this has occurred?

---

### Post by BluePlum on 2008-08-29
I don't think so, but would putting a password on boot options in the BIOS make this happen?

---

### Post by Crafty Kisses on 2008-08-29
Try removing it, and see what happens.

---

### Post by BluePlum on 2008-08-29
Wow man thanks, that fixed it! That's weird why it was happening tho... really weird...
Well enjoy your 21 thanks!

---

### Post by Crafty Kisses on 2008-08-29
> **BluePlum said:**
> Wow man thanks, that fixed it! That's weird why it was happening tho... really weird...
Well enjoy your 21 thanks!

I'm glad I could help. :)

---

