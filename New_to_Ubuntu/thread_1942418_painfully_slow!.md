---
title: "painfully slow!"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by wadie on 2012-03-17
Hi,

Ubuntu is being painfully slow for me!

I'm only running Firefox and installing two applications in Ubuntu Software Center..they keep going dark black (not responding). I'm not trying to do anything special..

I'm dual booting with Windows 7 and using Ubuntu 11.10.

System specs:
RAM: 2GB
Disk Space: 160GB - 18GB for Ubuntu
Processor: Intel Dual Core E4600 2.4GHz
GPU: Intel G33 Family Chipset

What is happening ? :\

---

### Post by 2F4U on 2012-03-17
Is anything running in the background? You can find out with a task manager or top or htop in a terminal. Check about RAM and CPU resource usage.

---

### Post by TenPlus1 on 2012-03-17
This may help:  [http://ubuntuforums.org/showpost.php?p=11773487&postcount=32](http://ubuntuforums.org/showpost.php?p=11773487&postcount=32)

---

### Post by hakermania on 2012-03-17
You had better not do other stuff (like running heavy applications) while installing software!

---

### Post by johnathansmith on 2012-03-17
Insert results from ```
user@user top
```, without installing something.

---

### Post by wadie on 2012-03-22
Sorry for the late response!
> 
top - 18:31:40 up 2 min,  1 user,  load average: 1.14, 0.75, 0.30
Tasks: 160 total,   1 running, 159 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.1%us,  1.2%sy,  0.0%ni, 95.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2041784k total,  1963588k used,    78196k free,   457904k buffers
Swap:   262140k total,     1560k used,   260580k free,   977756k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2293 wadie     20   0 1958m  56m  29m S   10  2.8   0:03.19 empathy-chat       
  933 root      20   0  182m  16m 5184 S    2  0.8   0:05.57 Xorg               
 1830 wadie     20   0  563m  85m  33m S    1  4.3   0:11.58 firefox            
 2062 wadie     20   0  514m  18m  11m S    1  0.9   0:00.60 gnome-terminal     
 2002 wadie     20   0  320m  14m 9872 S    1  0.7   0:00.47 notify-osd         
 1683 wadie     20   0 1209m  70m  27m S    0  3.6   0:07.19 compiz             
 2320 wadie     20   0 17324 1344  964 R    0  0.1   0:00.03 top                
    1 root      20   0 24436 2336 1332 S    0  0.1   0:00.61 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.17 kworker/0:0        
    5 root      20   0     0    0    0 S    0  0.0   0:00.27 kworker/u:0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    9 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/1:0 


And it's going a bit better since I posted this thread..

---

### Post by leMasoud on 2012-03-22
if you suspect it might be a memory issue,type "free" in terminal and see the result and check if there is enough memory to spend on related processes.
```
masoud@TECRA-M4:~$ free
             total       used       free     shared    buffers     cached
Mem:       2062008     894012    1167996          0      77596     376952
-/+ buffers/cache:     439464    1622544
Swap:      2095100          0    2095100

```
so if you think you need more "page file" or "swap" file or partition present check this out:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

