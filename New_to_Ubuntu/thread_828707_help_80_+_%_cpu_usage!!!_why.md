---
title: "help 80 + % cpu usage!!! why???"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by asharness on 2008-06-14
i am having a problem with cpu usage and i cant figure it out. please help!!
i have figure out kacpid (whatever that means) is using 80+%
Another thing. why is it saying three users? there is only one account?


top - 01:14:24 up 13 min,  3 users,  load average: 1.27, 1.30, 0.92
Tasks: 108 total,   2 running, 106 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3%us, 41.8%sy,  0.0%ni, 44.9%id,  0.0%wa, 12.0%hi,  0.0%si,  0.0%st
Mem:   1025112k total,   546672k used,   478440k free,    13260k buffers
Swap:   859436k total,        0k used,   859436k free,   241288k cached

scott@scott-desktop:~$  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
   33 root      11  -5     0    0    0 S   84  0.0  10:35.66 kacpid             
   34 root      10  -5     0    0    0 S    8  0.0   1:10.72 kacpi_notify       
 5387 root      15   0  384m  37m 6732 R    2  3.7   0:28.49 Xorg               
 6875 scott     15   0 91560  21m  12m S    2  2.1   0:02.08 gnome-terminal     
 6930 scott     15   0  155m  45m  20m S    1  4.5   0:19.76 firefox-bin        
 6895 scott     15   0  2368 1152  876 R    0  0.1   0:01.09 top                
    1 root      15   0  2952 1852  532 S    0  0.2   0:01.34 init               
    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.01 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.01 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper

---

### Post by spiderbatdad on 2008-06-14
the # of users is relative to how many sessions you have running. Your xsession (or desktop) is one. Each terminal session you open constitutes another user.

The other problem seems to be run away kacpi daemon. The result of a hardware detection problem.

I suggest editing the kernel line in /boot/grub/menu.lst by removing --quiet splash and replacing with acpi=off

You may also need to add acm=off

so you would have acpi=off acm=off

save the file and reboot.

---

### Post by asharness on 2008-06-14
i am a nuub to linux so please bare with me. I found the file but i am not locating the part you are refering to, where in this long list of stuff I dont understand will I find it

---

### Post by asharness on 2008-06-14
never mind io found it. so just replace quiet splash with acpi=off acm=off. so ithe whole line should look like this.

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9f358665-528e-4ab4-b995-d2d7f2fb8af5 ro acpi=off acm=off

correct????

---

### Post by spiderbatdad on 2008-06-14
```
## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=######### ro **lapic pci=routeirq**
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=######### ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I have shown in bold above the end of the kernel line. My options are slightly different. The Default kernel is the first one in the list. Next is recovery mode.

To edit the file you have to be in super user mode. Run this command:```
gksu gedit /boot/grub/menu.lst
```Save the file by clicking the floppy disk image at the top of the window when you are done.

---

### Post by spiderbatdad on 2008-06-14
You may also want to set the "#savedefault=true" Just above the kernel list.

---

### Post by asharness on 2008-06-14
cpu usage is down to about 70 %. better but thats still way high right

---

### Post by spiderbatdad on 2008-06-14
depends on what is running. An indexing program may be accessing the system. IDK if htop in available for kde, but you might look in your package manager. It is a little more informative and user friendly than top.

---

### Post by asharness on 2008-06-14
running an intel 3.2 duel with 1 g ram? does that help? checking packet manager. Thanks

---

### Post by asharness on 2008-06-14
oh yeah, what am I looking for in packet manager?

---

### Post by spiderbatdad on 2008-06-14
googled your kacpi issue. there are a lot of issues with it. A kernel bug apparently. You may have to wait for a good fix, or reinstall with Gutsy.

Personally I prefer gnome to kde, but I don't think that is the issue. It appears to be between the kernel itself and your hardware.

---

