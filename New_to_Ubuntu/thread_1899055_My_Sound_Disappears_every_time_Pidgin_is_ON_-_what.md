---
title: "My Sound Disappears every time Pidgin is ON - what's going on?"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by ajsoulmate on 2011-12-22
Hello,

My Machine: 
HP Laptop DV5

CPU: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz
Width: 64 bits
Memory: 4GB

OS: Ubuntu 10.04.3 LTS 64-bit
Kernel: 2.6.32-37-generic

Multimedia:
```
description: Audio device
product: 82801I (ICH9 Family) HD Audio Controller
vendor: Intel Corporation
physical id: 1b
bus info: pci@0000:00:1b.0
version: 03
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=HDA Intel latency=0
resources: irq:22 memory:df300000-df303fff

```


My problem starts whenever Pidgin is ON and I start another application say Skype. My sound completely goes OFF.
Sometimes, sound disappears even if Pidgin is the only application I run.

My Pidgin is version: Pidgin 2.9.0 (libpurple 2.9.0)

I'm not sure if some Pidgin Plug-ins are causing that? or perhaps it's something else?

Your help is appreciated, thanks in advance!

P.S.
Let me know if you need more details.

---

### Post by ajsoulmate on 2011-12-23
It's still happening and it's very annoying. Is there anything I can do to fix this? I removed Pidgin and installed it again (just in case it's the reason of all this) but that did not fix it.

---

### Post by boast on 2011-12-23
did you try having sound settings as a command, and have it be "aplay %s"

[img]http://cristian-radulescu.ro/wp-content/uploads/img/pidginpreferences.jpg[/img]

---

### Post by amjjawad on 2011-12-24
Try to run "pidgin" from the Terminal and see if there are some error message when the sound goes off, that is of course in case pidgin is the real cause of this problem. 

For me, I have never had this issue. I keep Ubuntu 10.04.3 installation on my PC so will give it a go and report back in case I got a similar issue.

Ubuntu 10.04 is a great OS by the way :)

---

