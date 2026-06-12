---
title: "Everything is sooo slow !"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by General_Ts0 on 2008-04-29
Clean install from Gutsy to Hardy and everything runs like molasses.  Ok, so not a CLEAN, as in DFFR clean, install but a during install, manually killed EXT3 partitions (left WinXP intact) and cleanly wrote over Gutsy.

so.... why does Hardy run so slow and what's a guy to do to troubleshoot.  Dell e510, 2.8 GHz, 512 RAM.

Skip the part about more RAM, Gutsy ran fine and only used < 100 MB

---

### Post by swoll1980 on 2008-04-29
General_Ts0's chicken is my fave as far as your problem can you specify what is running slow

---

### Post by alienexplorers on 2008-04-29
I thought Hardy was faster thn Gutsy in my opinion.

---

### Post by subzero316 on 2008-04-30
hmm...i 2 thought that hardy was more resource saving.

---

### Post by General_Ts0 on 2008-04-30
well for instance, Opening Firefox takes 25 seconds, opening update manager, it's still opening and connecting 60 seconds later, opening myhome folder takes 30 seconds.

Clicking on the "start" menu (applications) is a 10 second response between each submenu opening up when I mouse-over.

That's just a start.

---

### Post by bojac6 on 2008-04-30
I am having the same problem.  Even typing takes a few seconds between pressing the key and the letter appearing.  The only thing that is not ridiculously slow is that the mouse pointer moves with my movements, but even mousing over something that usually responds to a mouse over (borders around quick launch buttons, menus highlighted, that sort of thing) takes a good 3-5 seconds for the effect to appear.  Clicking on menus takes 10 seconds or so to open up.  Gutsy worked fine on the machine.

---

### Post by wdaniels on 2008-04-30
Are you seeing a lot of disk I/O or CPU usage, or both?
Is it only with Firefox running?  If so, see [here]("https://bugs.edge.launchpad.net/ubuntu/+source/firefox-3.0/+bug/215728").
Is it the same if you switch Compiz off?

Hardy runs quite quickly on my Asus Eee with 630MHz processor and 512Mb RAM so that's definitely not the problem.

---

### Post by MikeyXX on 2008-04-30
If you've done an essentially clean install, do it again. Wipe the machine and go again. Something may have corrupted during install.

I installed Gutsy once, it ran chunky, had every intention of giving up on it but then had a problem that required that I reinstall anyway. When I did, it installed and was smooth as glass.

---

### Post by bojac6 on 2008-04-30
Firefox has nothing to do with my problem at least, I haven't even tried to open it given how slow it all is.  Both of my CPUs are running at about 40% (took me about 5 minutes to open system monitor) when there is nothing open but system monitor.  Looking into fresh install, it was just an upgrade from Gutsy so I may download the normal install file

---

### Post by wdaniels on 2008-04-30
Note that you can use the terminal command "top" to check processor usage when the GUI is too slow. If you're happy to try another install, let's wait and see then...

---

### Post by bojac6 on 2008-04-30
Well, I'm hoping to avoid a fresh install, but if I'm out of options, it's not a big deal.  

Also, terminal is just as slow as the GUI.

---

### Post by General_Ts0 on 2008-04-30
Ya, opening terminal takes 10-15 seconds.  Good call, dude, after reboot only 35 MB free, what gives ?


> top - 20:45:59 up 3 min,  2 users,  load average: 0.34, 0.44, 0.19
Tasks: 117 total,   2 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.4%us,  1.3%sy,  0.0%ni, 98.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    514120k total,   477132k used,    36988k free,    10804k buffers
Swap:  1004052k total,        0k used,  1004052k free,   208828k cached

tso@bulldog:~$  PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5254 root      20   0  124m  65m  18m S    3 12.9   0:13.66 Xorg               
 2184 root      15  -5     0    0    0 S    0  0.0   0:00.04 scsi_eh_0          
 5574 tso       20   0 21732  14m 5784 S    0  2.8   0:02.34 compiz.real        
 5785 tso       20   0 68404  19m  10m R    0  3.9   0:00.56 gnome-terminal     
 5808 tso       20   0  2308 1116  852 R    0  0.2   0:00.22 top                
    1 root      20   0  2844 1692  544 S    0  0.3   0:01.92 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.16 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   47 root      15  -5     0    0    0 S    0  0.0   0:00.02 kblockd/0          



---

### Post by bojac6 on 2008-04-30
Well, a fresh install fixed it, now I just need to get all my settings back the way I like them.

---

