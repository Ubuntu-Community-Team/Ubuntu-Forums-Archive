---
title: "Something is eating my RAM."
date: 2013-07-10
forum: New to Ubuntu
---

### Post by macmus on 2013-07-10
Hi,

I think something is eating my Ram.  I cannot simply see it from top or ps aux but I see result.

I have:

```

KiB Mem:   8038232 total,  2968656 used,  5069576 free,   144364 buffers
KiB Swap:  4052988 total,        0 used,  4052988 free,  1559956 cached

```

When i use my applciation and force External Memory counter drop to 0 (with e.g Virtual Box, Rendering apps etc) my HDD starts go crazy and system becomes totaly unresponsive.

if i do swapoff and the counter reaches 0 system dies. :(

Could anyone help me debug it ?

---

### Post by Cheesemill on 2013-07-10
What application are you getting your above results from?

Can you post the output of...
```
free -m
```

---

### Post by snowpine on 2013-07-10
Unless I am completely misreading the results, you have **plenty** of RAM free (over 5gb!!) so I don't see the problem?

---

### Post by macmus on 2013-07-10
the problem is when I use it all wth application. When ram runs out due to applications (Virtual Box .. etc).
MY hdd overwhealms the PC which is eventually becming unresponsive.

```

lech@HP-EliteBook:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7849       5983       1866          0         98       1926
-/+ buffers/cache:       3958       3891
Swap:         3957          0       3957

```

---

### Post by snowpine on 2013-07-10
^---- According to your 'free -m' you have 3.8gb available RAM, as I understand it. (I used [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/) as my guide to interpret these numbers.)

If you are going to run a bunch of virtual machines, then you need sufficient RAM for the sum of each machine's virtual RAM, PLUS a sufficient amount for the "host" operating system (Ubuntu). Assuming your motherboard can go over 8gb, more RAM is inexpensive and would massively upgrade your capability to run multiple virtual machine "guests" OS's simultaneously.

From your description of symptoms, it sounds like, when your RAM gets full, your system goes to swap on the hard drive. Swap by its nature will be substantially slower than RAM (but better than crashing). 

If you want to reduce your RAM usage (rather than upgrade your RAM to meet your needs) then use your favorite system monitor (such as 'top') to find out what is using the most RAM. Then find a way to reduce or eliminate these processes. (For example you could reduce the memory allotment of each VM, or run fewer simultaneous VM's.) Post the output here if you want some tips.

---

### Post by CharlesA on 2013-07-10
> **snowpine said:**
> 
If you are going to run a bunch of virtual machines, then you need sufficient RAM for the sum of each machine's virtual RAM, PLUS a sufficient amount for the "host" operating system (Ubuntu). Assuming your motherboard can go over 8gb, more RAM is inexpensive and would massively upgrade your capability to run multiple virtual machine "guests" OS's simultaneously.

From your description of symptoms, it sounds like, when your RAM gets full, your system goes to swap on the hard drive. Swap by its nature will be substantially slower than RAM (but better than crashing). 

If you want to reduce your RAM usage (rather than upgrade your RAM to meet your needs) then use your favorite system monitor (such as 'top') to find out what is using the most RAM. Then find a way to reduce or eliminate these processes. (For example you could reduce the memory allotment of each VM, or run fewer simultaneous VM's.) Post the output here if you want some tips.

Last time I heard of running out of memory with vbox resulted in the VM getting killed off. I wonder if they changed it to use swap now.

@OP: If you are serious about running a bunch of VMs, upgrade your memory to support the number of machines you want to run.

---

### Post by DogMatix on 2013-07-10
> **macmus said:**
> the problem is when I use it all wth application. When ram runs out due to applications (Virtual Box .. etc).
MY hdd overwhealms the PC which is eventually becming unresponsive.

```

lech@HP-EliteBook:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7849       5983       1866          0         98       1926
-/+ buffers/cache:       3958       3891
Swap:         3957          0       3957

```

Then quite simply the 'something' eating your RAM is the applications you are running. I have plenty of RAM but if I launch  Virtual Box and dedicate half my memory to it then launch GIMP and open a few A1 300dpi images and start editing them whilst watching a movie on VLC I'd have problems as well.

How much RAM are you allowing Virtual Box to use?

---

