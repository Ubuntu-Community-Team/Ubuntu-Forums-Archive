---
title: "Where can I see my PC specs?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Solais on 2008-09-13
Wanted to update my Video Card Driver etc but i forgot witch series was it, where can I see my ram/video card and etc?:confused:

---

### Post by natman on 2008-09-13
Do this (in a terminal )
> sudo apt-get install hwinfo
hwinfo --short

---

### Post by Solais on 2008-09-13
> **natman said:**
> Do this (in a terminal )

now what :confused:

---

### Post by natman on 2008-09-13
Ok, open a terminal can you do that? if so type in
> sudo apt-get install hwinfo
Then type your password in and hit enter, then possible Y if the terminal asks you to agree, after
type in
> hwinfo --short

---

### Post by acidsolution on 2008-09-13
```
$sudo lshw -html > your-file-name.html
```
from this you can see your pc info in html format 
open the file in browser

---

### Post by Solais on 2008-09-13
Thanks guys :)

---

### Post by acidsolution on 2008-09-13
Mark the thread as solved if you find your answer

---

### Post by starcannon on 2008-09-13
If you want a hardware information app that has a gui

```
sudo apt-get install sysinfo
```

You'll then find it in the menu's at {Applications>System Tools>Sysinfo}

Enjoy.

---

### Post by Speed Demon on 2008-09-13
as other person said, lshw -html works. Or you can do lshw to see all your specs but in terminal not html file to see in browser (couple hundred lines in terminal fullscreen) or lshw -C device-name-here to show ONLY one device's specs for instance lshw -C processor to see processor output, which for me displays
```
joshua@joshua-desktop:~$ lshw -C processor
WARNING: you should run this program as super-user.
  *-cpu                                            
       product: Intel(R) Pentium(R) 4 CPU 3.20GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 15.6.5
       serial: 0000-0F65-0000-0000-0000-0000
       size: 2400MHz
       capacity: 2400MHz
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl est tm2 cid cx16 xtpr lahf_lm cpufreq
       configuration: id=1
     *-logicalcpu:0
          description: Logical CPU
          physical id: 1.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 1.2
          width: 64 bits
          capabilities: logical
```
Have fun lol

---

### Post by donec on 2008-09-13
You can also install sysinfo via the synaptic package manager. Just search for sysinfo in the synaptic package manager and it will show up.

---

