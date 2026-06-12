---
title: "Why are my apps so much slower?"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by Papa-san on 2008-09-29
I have a dual boot system. It is a Dell 1525 that came with the Vista Virus pre-installed. I added Hardy and it worked pretty well right off the bat. (It came with the Intel PRO/Wireless 3945ABG wireless card, which is pretty much plug-n-play...) It was running everything at about the same speed as the 'other one'...

I was disappointed in the speed Vista gave me considering it has 2Gb of memory and a Dual core processor. Then I discovered that Vista, by default, only loads one of those cores. I changed that and got rid of some of the bloat, and now it is really pretty quick. (I can run HalfLife 2 episode 2 with no lag, so even though it has integrated video, it's not too bad...)

Now, however, my wife is complaining about how slow Ubuntu is. It's been a REALLY hard sell to get her to even use it, and I don't want her to turn her back on it completely... I have timed a few different tasks, and the applications in Ubuntu ARE significantly slower. Most noticeably Firefox... ('Cause that is the one we tend to use most.) 

I am relatively sure that I have a lot of things that are not running optimally. I'm not even sure if it's 32 bit or a 64 bit. 

I would really appreciate it if someone might be able to help me optimize this thing so I can begin to use some of the 'Wow' stuff that Ubuntu has to offer...

---

### Post by Pro-reason on 2008-09-29
It is true that Firefox, that gem of open source, is in fact not very optimised for Linux, and doesn't run very fast.  You'd do well to use Konqueror, Opera, Epiphany, or another browser, unless you are addicted to Firefox's add-ons.  Only use Firefox on Windows.

You might also want to try turning off 3D effects if they are slowing things down.  Another thing to check is whether your processor is running hyper-threading (if capable of it).  Open the System Monitor and check whether unnecessary processes are running.

P.S. Read the first sentence again.

---

### Post by Papa-san on 2008-09-29
Yeah, I know that firefox is pretty slow. What I'm talking about is that there is a noticeable difference between using it in Vista compared to Ubuntu. I have a few lines in my 'lshw' that tell me I have illegal vendors or something, and it doesn't seem to know whether or not it is a 32 bit or 64 bit system...

I checked the System monitor and didn't see anything that stood out...

---

### Post by Crafty Kisses on 2008-09-29
Post the results of this command:
```
top
```
It could be a resource issue.

---

### Post by Papa-san on 2008-09-30
Watched it for a bit and got 2 screenshots:

It does say there is 1 zombie, for what it's worth...

---

### Post by Papa-san on 2008-10-01
So is there anyone who might want to help me work through this?

---

### Post by Papa-san on 2008-10-10
Bump

---

### Post by TheLions on 2008-10-10
install Swiftweasel -->much faster

but first find out which cpu you own with lshw command

---

### Post by Papa-san on 2008-10-10
I'll try swiftweasel. Here's the info on the processor:```
john@john-1525n:~$ lshw
WARNING: you should run this program as super-user.
john-1525n                
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2017MiB
     *-cpu
          product: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
```

---

### Post by Ptero-4 on 2008-10-10
You got a Pentium DualCore x64 CPU.

---

### Post by Papa-san on 2008-10-10
Thanx,

So is there any information I can supply that will let you know if I have any of the other hardware configured improperly?

I have many things running at 32 bits. I don't know if that makes any difference or not.

 Any ideas about this:```
*-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 9.3
                bus info: pci@0000:02:09.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
           *-generic UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 9.4
                bus info: pci@0000:02:09.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
```

---

