---
title: "Pidgin Often &quot;Randomly&quot; Crashes."
date: 2008-08-07
forum: New to Ubuntu
---

### Post by osc1882 on 2008-08-07
There is another post about this but it has been made read only, so I'm starting a new one.

Pidgin Randomly Crashes. Of course I know there is nothing truly random with computers, but that's how it seems from my end. I have no plug ins right now. I used to have a bunch but I took them all off for trouble shooting reasons. I un-installed and re-installed hoping that it would delete all settings for the program, but there seems to be some settings file somewhere?? I can't tell. It just started happening one day, the best I can tell. But Ubuntu awesomely updates so often that it is hard to tell/remember. It seems to crash some times when I send a message, or get one.... I also think maybe it does when someone comes online???

So if anyone could help that it would mean a lot. I switched to aMSN for a while (even tho it doesn't support other networks I use) but the last few days aMSN won't connect for... reasons unknown to me. So it's back to crashing.

Thanks in advance.

---

### Post by Ryadt on 2008-08-07
Try reinstalling pidgin again. Make sure you delete its hidden folder (.purple) in your home directory.
Concerning amsn, there has been a problem on the one in the repos. You can download the version on their website
[http://www.amsn-project.net/linux-downloads.php](http://www.amsn-project.net/linux-downloads.php)
choose the tcl/tk 8.4 installer.

---

### Post by Crafty Kisses on 2008-08-07
Possible resource issue, post the following output:
```
top
```

---

### Post by osc1882 on 2008-08-07
.Purple .... I would have never guessed that. I mean I knew that home folder had folders starting with "." that are hidden and holds settings files and other things like that, but I would have never guessed .purple. Anyways, I have deleted the folder/reinstalled the program and I will post back to let everyone know if it crashes or not. It Might take me a day or two to know for sure seeing that I am going to sleep soon.

How do you install a .package file?




Out Put for Top:
grammatrain@tprb:~$ top

top - 01:46:19 up 3 days,  2:10,  2 users,  load average: 0.05, 0.21, 0.15
Tasks: 143 total,   2 running, 141 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.6%us,  0.5%sy,  0.0%ni, 94.8%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   3631056k total,  2815776k used,   815280k free,   801396k buffers
Swap:   979956k total,    39808k used,   940148k free,  1542976k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6374 root      20   0  370m  62m  10m S    8  1.8  56:50.95 Xorg               
 6779 grammatr  20   0  111m  52m  12m S    1  1.5  51:34.11 compiz.real        
15693 grammatr  20   0  189m  72m  21m S    1  2.0   0:11.88 firefox            
15864 grammatr  20   0 73724  19m  10m R    1  0.6   0:00.22 gnome-terminal     
15893 grammatr  20   0  2308 1136  852 R    1  0.0   0:00.02 top                
    1 root      20   0  2844 1692  544 S    0  0.0   0:01.28 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.90 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:04.64 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.84 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.66 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:01.02 kblockd/0

---

### Post by Nevyn on 2008-08-07
How to install; great guides here:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

When you type in "top" in the terminal, you should have Pidgin running. What I think Codename was after was how much CPU% Pidgin was using (the top command shows you which resources every running application is using.

Please start Pidgin and type in "top" again, end copy-paste it here.

---

### Post by osc1882 on 2008-08-08
It's still crashing sadly.

grammatrain@tprb:~$ top

top - 01:54:35 up 4 days,  2:18,  2 users,  load average: 0.23, 0.93, 0.62
Tasks: 149 total,   1 running, 148 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.9%us,  0.2%sy,  0.0%ni, 96.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3631056k total,  3465908k used,   165148k free,   768208k buffers
Swap:   979956k total,    39808k used,   940148k free,  2171716k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6374 root      20   0  364m  62m  11m S    4  1.8  75:37.17 Xorg               
 6779 grammatr  20   0  108m  52m  12m S    1  1.5  59:26.82 compiz.real        
29131 grammatr  20   0 2611m  17m 8060 S    1  0.5   0:04.89 EAC.exe            
30997 grammatr  20   0  137m  62m  19m S    1  1.8   0:04.93 firefox            
31011 grammatr  20   0 64464  18m  10m S    1  0.5   0:00.20 gnome-terminal     
31031 grammatr  20   0  2308 1136  852 R    1  0.0   0:00.02 top                
 6684 grammatr  20   0 40016  10m 7800 S    0  0.3   0:17.72 gnome-settings-    
    1 root      20   0  2844 1692  544 S    0  0.0   0:01.30 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:01.24 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:06.52 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:01.10 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.88 events/1           


There it is. Pidgin is running, but I don't see it on that list.

---

### Post by s3a on 2008-08-08
Remove everything you have previously attempted and try simply installing from a .deb file.

Here is a .deb file of Pidgin 2.4.3:
[http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

---

