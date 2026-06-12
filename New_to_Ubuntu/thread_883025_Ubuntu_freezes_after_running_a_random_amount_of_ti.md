---
title: "Ubuntu freezes after running a random amount of time"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by sharad.sharma on 2008-08-07
I set up a dual boot with Windows XP and Ubuntu 8.04.
After a random amount of time,Ubuntu freezes and there is no response of the keyboard/mouse events.Audio playback stops.A restart solves the issue.Can this be a problem with Ubuntu?(or just a coincidence and actually a hardware problem)

How do I start with basic troubleshooting for this problem in Ubuntu.Please help.

---

### Post by Tatty on 2008-08-07
It may be worth running a memtest (you can select this from the grub menu when you start your comp) to check for faulty RAM in your machine.

Are there any sort of patterns you can identify in the freezing, such as a set time or certain actions you perform before it happens?

Has this only just started happening, or has it been like this since install?

Also, are you running compizfusion (desktop effects)?

---

### Post by sharad.sharma on 2008-08-07
OK,I'll perform the memtest and update this thread.

No,the system freezes just randomly without a set pattern.The applications running are usually Amarok,Pidgin,Utorrent through Wine,Firefox.

I installed Ubuntu 8.04 a week ago and this has started happening since the past two days.(I install all updates as recommended by the update manager.Is that OK?)

I ran compiz for a while which slowed the system down a bit..so I switched to No effects.

---

### Post by Crafty Kisses on 2008-08-07
Yeah run a memetest and also post the following output:
```
top
```
It could be a resource issue but I highly doubt that, but you never know.

---

### Post by sharad.sharma on 2008-08-07
Rebooted to run the memtest..It ran for 48 seconds and then the WallTime stopped clicking at Pass 3 - Test 37%. WallTime isn't supposed to stop clicking due to any errors in the RAM..right?
Waited for a while and then restarted and selected the Ubuntu OS to boot.

The system hung at ***Starting up..***
So I switched it off and rebooted after 7-10 minutes.The system started successfully then.

Output of top :

```
top - 01:23:44 up 8 min,  2 users,  load average: 0.16, 0.29, 0.21
Tasks:  99 total,   3 running,  96 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.6%us,  0.4%sy,  0.0%ni, 97.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    766448k total,   619648k used,   146800k free,    16176k buffers
Swap:        0k total,        0k used,        0k free,   324036k cached
B
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.26 init                                                            
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                        
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                     
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                     
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                      
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 events/0                                                        
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                         
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0                                                       
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                          
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                    
  119 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                         
  156 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                         
  157 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                         
  158 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                         [319 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                         
  156 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                         
  157 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                         
  158 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                         
  199 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                           
 1457 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                   
 1461 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                           
 1491 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 ata/0                                                           
 1494 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                         
 1670 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                       
 1673 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 scsi_eh_1                                                       
 2577 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kjournald                                                       
 2802 root      16  -4  2412  960  380 S  0.0  0.1   0:00.34 udevd                                                           
 3140 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                       
 4445 root      20   0  1716  512  440 S  0.0  0.1   0:00.00 getty                                                           
 4446 root      20   0  1716  512  440 S  0.0  0.1   0:00.00 getty                                                           
 4450 root      20   0  1716  508  440 S  0.0  0.1   0:00.00 getty                                                           
 4451 root      20   0  1716  504  440 S  0.0  0.1   0:00.00 getty                                                           
 4455 root      20   0  1716  512  440 S  0.0  0.1   0:00.00 getty 
```

---

### Post by Tatty on 2008-08-07
It is beginning to sound like a hardware problem due to the memtest freezing.  Do you have any spare RAM you can swap over?

Alternatively it is possible that the CD image your installed from is corrupted somehow... try running an integrity check on the CD you installed with (if you still have it).

---

### Post by sharad.sharma on 2008-08-07
No spare RAM but I am using two chips (256 MB and 512MB).So I can probably remove one at a time and check if the other is OK.

I got the Ubuntu 8.04 CD from a friend(who got it through Shipit).Yes I have it and will run the check

---

### Post by Crafty Kisses on 2008-08-07
> **sharad.sharma said:**
> No spare RAM but I am using two chips (256 MB and 512MB).So I can probably remove one at a time and check if the other is OK.

I got the Ubuntu 8.04 CD from a friend(who got it through Shipit).Yes I have it and will run the check

That's what I was thinking, could be bad RAM.

---

### Post by markbuntu on 2008-08-07
Mismatched ram caused random system freezes for me. Since I changed to all the same size ram about a month ago I have had zero system freezes.

---

