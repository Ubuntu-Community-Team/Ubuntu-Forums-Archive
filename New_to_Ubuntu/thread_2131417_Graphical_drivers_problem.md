---
title: "Graphical drivers problem"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by pavelangelov on 2013-04-01
Hello everyone! :)

My name is Pavel Angelov and I'm new with all linux things. I like web programming and I decided to learn some additional stuffs. For start i chose Ubuntu 12.10.

I installed the Ubuntu, installed some updates, but when i tried to install my nvidia drivers (by apt-get install nvidia-current-updates, that i saw in a tutorial) my deck in left disappeared. So I'm asking for help - step by step. Do I need a fresh install of Ubuntu? Or what do i need? The PC is laptop - Acer V3-571G, Nvidia M630GT.

Thanks in advance and good day to you :)

Pavel =)

---

### Post by papibe on 2013-04-01
Hi pavelangelov.

Could you post the result of these 2 commands?
```
lsmod | grep -i nvidia

lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by pavelangelov on 2013-04-02
Thanks for the quick answer :)

So here we are:

from lsmod | grep -i nvidia
output:
nvidia 11257760 0

from lspci -nnk | grep -iA2 vga
output:
00:02.0 VGA compatible controller [0300] Inte corporation 3rd Gen Core processor Graohics Controller [8086:0166](rev 09) 
Subsystem: Acer Incorporated [ALI] Device [1025:0647]
Kernel driver in use: i915

01:00.0 VGA compatible controller [0300] NVIDIA Corporation GF108 [Ge Force GT 630M] [10de:0de9](reva1) 
Subsystem: Acer Incorporated [ALI] Device [1025:0648]
Kernel driver in use: nvidia

---

### Post by pavelangelov on 2013-04-02
It's me again, but my topic has gone deeper. 

Anyone for the rescue :)

---

### Post by papibe on 2013-04-02
Your computer has[ Nvidia Optimus]("http://www.nvidia.com/object/optimus_technology.html").

Take a look at this [tutorial]("https://wiki.ubuntu.com/Bumblebee") on how properly install the drivers in your situation.

In 12.10 it is best to start installing this:
```
sudo apt-get install linux-headers-generic
```

Let us know how it goes.
Regards.

---

### Post by pavelangelov on 2013-04-03
Now everything is fine :) Thanks for the help! Now I'm going to learning it hard :P

---

