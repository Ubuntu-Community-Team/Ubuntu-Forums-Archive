---
title: "what processes can I turn off for better performance?"
date: 2014-11-05
forum: New to Ubuntu
---

### Post by marchello_lippi2 on 2014-11-05
Hi all, 

what processes can I turn off for better performance?


$ top -u root

  PID &#1050;&#1054;&#1056;.   PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                                                     
 1358 root      20   0  210064  87360  28696 S   2,3  5,0   8:56.41 Xorg                                                                                                                        
  583 root      20   0       0      0      0 S   0,3  0,0   0:09.38 rts5139-polling                                                                                                             
    1 root      20   0    4576   2532   1412 S   0,0  0,1   0:03.65 init                                                                                                                        
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kthreadd                                                                                                                    
    3 root      20   0       0      0      0 S   0,0  0,0   0:01.39 ksoftirqd/0                                                                                                                 
    5 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:0H                                                                                                                
    7 root      20   0       0      0      0 S   0,0  0,0   0:04.07 rcu_sched                                                                                                                   
    8 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh                                                                                                                      
    9 root      rt   0       0      0      0 S   0,0  0,0   0:00.42 migration/0                                                                                                                 
   10 root      rt   0       0      0      0 S   0,0  0,0   0:00.05 watchdog/0                                                                                                                  
   11 root      rt   0       0      0      0 S   0,0  0,0   0:00.04 watchdog/1                                                                                                                  
   12 root      rt   0       0      0      0 S   0,0  0,0   0:00.07 migration/1                                                                                                                 
   13 root      20   0       0      0      0 S   0,0  0,0   0:00.90 ksoftirqd/1                                                                                                                 
   15 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/1:0H                                                                                                                
   16 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 khelper                                                                                                                     
   17 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kdevtmpfs                                                                                                                   
   18 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 netns                                                                                                                       
   19 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 writeback                                                                                                                   
   20 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kintegrityd                                                                                                                 
   21 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                      
   23 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kblockd                                                                                                                     
   24 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ata_sff                                                                                                                     
   25 root      20   0       0      0      0 S   0,0  0,0   0:00.00 khubd                                                                                                                       
   26 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 md                                                                                                                          
   27 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 devfreq_wq                                                                                                                  
   28 root      20   0       0      0      0 R   0,0  0,0   0:09.18 kworker/0:1                                                                                                                 
   30 root      20   0       0      0      0 S   0,0  0,0   0:00.00 khungtaskd                                                                                                                  
   31 root      20   0       0      0      0 S   0,0  0,0   0:00.80 kswapd0                                                                                                                     
   32 root      25   5       0      0      0 S   0,0  0,0   0:00.00 ksmd                                                                                                                        
   33 root      39  19       0      0      0 S   0,0  0,0   0:00.75 khugepaged                                                                                                                  
   34 root      20   0       0      0      0 S   0,0  0,0   0:00.00 fsnotify_mark                                                                                                               
   35 root      20   0       0      0      0 S   0,0  0,0   0:00.00 ecryptfs-kthrea                                                                                                             
   36 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 crypto                                                                                                                      
   48 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kthrotld                                                                                                                    
   72 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 deferwq                                                                                                                     
   73 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 charger_manager                                                                                                             
   92 root      20   0       0      0      0 S   0,0  0,0   0:08.13 kworker/1:2                                                                                                                 
  122 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kpsmoused                                                                                                                   
  123 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_0                                                                                                                   
  124 root      20   0       0      0      0 S   0,0  0,0   0:00.00 scsi_eh_1                                                                                                                   
  136 root      20   0       0      0      0 S   0,0  0,0   0:01.10 jbd2/sda1-8

---

### Post by ajgreeny on 2014-11-05
I don't know, is my answer to that specific query; nothing sticks out as a major problem in that list.

However, rather than doing things this way you could install bum (boot-up-manager) which gives you the easy option to stop many services from running at boot, if you want to, and if things that you need stop working you can run bum again and reselect them to start at boot once more.

PS:
It will help us to read that list and be able to see the memory and cpu usage of the processes if you edit the post and put the list in code tags.  See my signature below for how to do that.

---

### Post by papibe on 2014-11-05
Hi marchello_lippi2.

A few ideas:

IMHO, I'd start by taking a look at your hardware, and your choice of desktop. Could you tell us about that?

It looks like your hard drive is encrypted, right? Depending of your hardware it could be a performance hit.

In order to take a look at 'heavy process' I'd recommend using this command:
```
top -n5 -b | grep -v ^KiB  | sort -rg -k 9,9 | sort -k 12,12 -u | sort -rg -k 9,9 | head -n 15
```
This would display to 15 top CPU process eaters.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Rob Sayer on 2014-11-06
According to a quick look at your other posts you're running a conky.  That'd be a good place to start trimming.  If it includes any video effects turn *all* those off as well.  LXDE runs fast and best when kept simple and ugly.

You can also try different widget themes in preferences->customize look and feel.  Some of them may run faster, like clearlooks.

---

### Post by ibjsb4 on 2014-11-06
A way to play with running processes.

Open up your 'System Monitor' and go to Processes.  From there, you can kill any process that you want.  If killing a process borks your system, all you have to do is reboot and it will be restored to default.  No harm done.

To answer your question.  I have not found this to have a positive effect on performance on my installs.  Maybe if I clocked it, I could see a few milli seconds here and there, but for me, I just do a visual.

I find using leaner packages (software) is the way to go.  

You could also try your hand at tweaking the kernel.
[https://www.google.com/search?client=ubuntu&channel=fs&q=kernel+tweaks+linux&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=kernel+tweaks+linux&ie=utf-8&oe=utf-8)

Just be prepared for breakage.

---

### Post by kalehrl on 2014-11-06
The best way to reduce CPU load is to start with a minimal system and then add a light desktop environment such as LXDE.
That's the way I do it.
I install minimal command line system using mini.iso, then add lxde-core with --no-install-recommends and after that tweak it a little bit.

---

### Post by ibjsb4 on 2014-11-06
> **Rob Sayer said:**
> LXDE runs fast and best when kept simple and ugly.
Beauty is in the eye of the beholder :)

---

### Post by vasa1 on 2014-11-06
> **Rob Sayer said:**
>  ...
You can also try different widget themes in preferences->customize look and feel.  Some of them may run faster, like clearlooks.
Clearlooks doesn't come with a gtk3 folder. I don't know why it's included in the distro.

Edit: Lubuntu probably can't do anything about it: it's part of the gtk2-engines package: *apt-cache show gtk2-engines*. And there's also *apt-cache show clearlooks-phenix-theme*. I should look at that to see if I can't make things even more frugal :)

---

### Post by Rob Sayer on 2014-11-07
> **ibjsb4 said:**
> Beauty is in the eye of the beholder :)

I actually *like* the idea of a desktop environment that works very much like Mac OS X yet looks like a butt ugly 90's Windows desktop.

---

### Post by ibjsb4 on 2014-11-07
Two days and no reply from the OP.  Where's this thread going Rob?

---

### Post by papibe on 2014-11-07
Hi all,

I just want to remind everybody that this is a support thread, so please try to take care of marchello_lippi2's concern as much as you can.

Aesthetic assessment are not (so far) a concern of the OP.

Thanks in advance.

---

