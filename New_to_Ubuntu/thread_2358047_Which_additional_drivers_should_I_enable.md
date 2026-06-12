---
title: "Which additional drivers should I enable?"
date: 2017-04-09
forum: New to Ubuntu
---

### Post by yorch95 on 2017-04-09
which driver should i select under "additional drivers". In the  command line, i entered "ubuntu-drivers-devices" and turns out my model  is: GM107M [GeForce GTX 860M]. Also it shows "driver   : nvidia-375 -  distro non-free recommended".

  
By default, I have the X.Org X server. I assume the right thing to do would be select my recommended NVIDIA driver, right? 

  
Another question i have is that there are also choosable options  under "Unknown: Unknown" in "Additional Drivers" as well. Should i select the processor microcode  firmwarefor intel CPUs (proprietary)? or leave it as it is and don't use it? 

  
Consider the fact that i will be playing steam games (rocket league to be more specific). 

Also, i have ubuntu 16.04.2 LTS

---

### Post by kc1di on 2017-04-09
I would try the recommended driver for your Nvidia card first.  The microcode is not needed unless your having trouble with overheating or some other problems with cpu function.
good luck.

---

### Post by RobGoss on 2017-04-09
The recommend driver option should work

---

### Post by yorch95 on 2017-04-09
> **kc1di said:**
> I would try the recommended driver for your Nvidia card first.  The microcode is not needed unless your having trouble with overheating or some other problems with cpu function.
good luck.

excellent. thanks a lot!

---

### Post by mastablasta on 2017-04-10
> **kc1di said:**
> I would try the recommended driver for your Nvidia card first.  The microcode is not needed unless your having trouble with overheating or some other problems with cpu function.
good luck.

not true. expecially not without knowing the exact chip and model. from Debian documentation found at:

[SIZE=2][https://wiki.debian.org/Microcode](https://wiki.debian.org/Microcode)
[/SIZE]

> It is very difficult to know for sure whether you need a microcode update or not, but it is not safe at all to just ignore them.  You might not notice their effect and have precious data silently corrupted, or an important program silently misbehave.  Or you could experience one of those unexplainable and infrequent software issues (such as kernel oops, application segfaults) or hardware issues (including sudden reboots and hangs).

---

### Post by kc1di on 2017-04-10
> **mastablasta said:**
> not true. expecially not without knowing the exact chip and model. from Debian documentation found at:

[SIZE=2][https://wiki.debian.org/Microcode](https://wiki.debian.org/Microcode)
[/SIZE]

I Stand corrected and have applied the microcode to my own machine , an amd. thank you ;)

---

### Post by poorguy on 2017-04-10
I will always give the open source drivers a chance and see how they work and if the open source drivers are working without problems then I will keep using them.

I will only switch to the proprietary drivers as needed if problems with open source drivers arise.

---

