---
title: "computer moving slow"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by misswham on 2008-09-18
My ubuntu all of a sudden started loading and moving slow.  It is acting like when i had a lot of spyware on my windows version. Surfing is moving almost like dialup.  What might be the problem?

---

### Post by overdrank on 2008-09-18
> **misswham said:**
> My ubuntu all of a sudden started loading and moving slow.  It is acting like when i had a lot of spyware on my windows version. Surfing is moving almost like dialup.  What might be the problem?

Hi and have you installed, updated or added any hardware? What are some system specs? Just asking questions to maybe narrow down the issue.

---

### Post by Sef on 2008-09-18
> Hi and have you installed, updated or added any hardware? What are some system specs? Just asking questions to maybe narrow down the issue.

1) Or have you installed,or updated any software after which your computer started running slow?

2a) Appliations > Accessories > Terminal

then type in this code: ```
top
```

2b) If you prefer a GUI to the Terminal, then do this:  System > Administration > System Monitor

---

### Post by misswham on 2008-09-18
Yes I have always accepted the updates as they come.  I thought I was supposed to do that.  I get updates about twice a week and yes I accepted them.  I did the top command and i got 

top - 22:22:07 up 20 min,  2 users,  load average: 0.29, 0.32, 0.16
Tasks: 126 total,   1 running, 125 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.9%us,  0.5%sy,  0.0%ni, 95.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    905280k total,   590196k used,   315084k free,    18232k buffers
Swap:  1919728k total,        0k used,  1919728k free,   340184k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6020 root      20   0 55764  28m 8128 S    4  3.2   0:08.26 Xorg               
 7140 aretha    20   0 58052  37m  10m S    1  4.3   0:07.30 compiz.real        
 7194 aretha    20   0 21088 8652 7356 S    1  1.0   0:01.02 geyes_applet2      
 7343 aretha    20   0 66464  16m  10m S    1  1.9   0:00.80 gnome-terminal     
 5903 root      20   0  3420 1140  988 S    1  0.1   0:00.12 hald-addon-stor    
 7073 aretha    20   0 37556  18m  12m S    1  2.1   0:02.38 gnome-panel        
 7158 aretha    20   0 31056  11m 8508 S    1  1.3   0:00.42 nm-applet          
 7297 aretha    20   0  149m  55m  19m S    1  6.3   0:10.01 firefox            
    1 root      20   0  2844 1692  544 S    0  0.2   0:01.44 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           

I havent a clue what I am looking at any ideas?

---

### Post by nowshining on 2008-09-18
have u tried a reboot after install of the updates?? you esp. will if the kernel is updated...

---

### Post by misswham on 2008-09-19
Always.  So I dont know what now.

---

### Post by cariboo on 2008-09-19
Could you repost the output of top using the code tags,You can click on the # sign in the advanced editor. You've got something using about 95.7% of your cpu's output, but without any formatting it is hard to tell what it is.

Jim

---

### Post by misswham on 2008-09-19
i dont see an advanced editor.  all i see is what i posted earlier.  can u tell me where it is?

---

### Post by misswham on 2008-09-19
top - 23:56:27 up  1:54,  2 users,  load average: 0.29, 0.45, 0.60
Tasks: 126 total,   1 running, 125 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.0%us,  1.9%sy,  0.0%ni, 89.9%id,  0.0%wa,  0.1%hi,  0.0%si,  0.0%st
Mem:    905280k total,   523564k used,   381716k free,    10920k buffers
Swap:  1919728k total,    39784k used,  1879944k free,   240796k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                               
 6020 root      20   0 64896  38m 8248 S    9  4.3   4:58.00 Xorg                                  
10160 aretha    20   0 66184  16m  10m S    2  1.8   0:00.88 gnome-terminal                        
 7140 aretha    20   0 61752  39m  10m S    2  4.5   2:13.60 compiz.real                           
 7194 aretha    20   0 21088 8756 7444 S    1  1.0   0:17.42 geyes_applet2                         
 9548 aretha    20   0  221m  96m  29m S    0 11.0   7:33.97 firefox                               
    1 root      20   0  2844 1692  544 S    0  0.2   0:01.44 init                                  
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                              
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                           
    4 root      15  -5     0    0    0 S    0  0.0   0:00.14 ksoftirqd/0                           
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                            
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                           
    7 root      15  -5     0    0    0 S    0  0.0   0:01.70 ksoftirqd/1                           
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                            
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0                              
   10 root      15  -5     0    0    0 S    0  0.0   0:00.08 events/1                              
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                               
   46 root      15  -5     0    0    0 S    0  0.0   0:00.10 kblockd/0                             
   47 root      15  -5     0    0    0 S    0  0.0   0:00.26 kblockd/1

---

### Post by Sef on 2008-09-19
1) Applications > Accessories > Terminal

Then paste or type in this code and post the results here:

```
uname -a
```2) What version of Ubuntu are you using?

3) Boot into GRUB (hit esc when it says to in boot up), then go choose an older kernel if you have one.   Next check top again and see if the problem is still there or not. 

4) There has been this problem reported with some versions of kernel 2.6.9.

---

### Post by misswham on 2008-09-19
2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

---

### Post by misswham on 2008-09-19
also I am not sure what version I am using all I know is Hardy.

---

### Post by myidbe on 2008-09-19
Just a stab in the dark here: 
I recently installed ubuntu (hardy) on a computer and made the swap partition to large. The computer then took a *lot* of time to do anything and the hard drive was noticeably spinning more often. I would defer to the opinion of some of the other guys here, but perhaps it could be this problem you're experiencing (though if you let ubuntu do the partitioning for you during setup, or if it's been a while since you installed this shouldn't normally be the problem..)

For example, in your output from "top" earlier, your swap partition is 1919728k:
```
Swap: 1919728k total, 0k used, 1919728k free, 340184k cached
``` 

My swap drive, for comparison, is 497944k for a primary ubuntu partition of 55GB and 512MB of RAM.

---

### Post by misswham on 2008-09-19
i am very confused now.  what can i do to correct the problem?  i partitiioned the harddrive myself.  does it sound as if i have too much on my harddrive the linux part?  i dont have much in my documents.  i have 12 gbs left on my harddrive.  on the linux part the xp part i am sure has much more room.

---

### Post by myidbe on 2008-09-20
Bump - a large swap partition *could* be your problem but I'm not sure how to say that it is definately so.

---

