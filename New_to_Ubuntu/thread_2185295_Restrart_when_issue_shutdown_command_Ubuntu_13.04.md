---
title: "Restrart when issue shutdown command Ubuntu 13.04"
date: 2013-11-01
forum: New to Ubuntu
---

### Post by sanitherayil on 2013-11-01
WhenI try to shutdown down the Ubuntu 13.04 the system restarted only. I cannot shut down the system. Please help.

---

### Post by protoss96 on 2013-11-02
You can always shutdown your PC with these two commands.
```
sudo shutdown -h now
```
OR
```
sudo poweroff
```

---

### Post by sanitherayil on 2013-11-07
thanks for your replay. it also make same result. the system is shutting down but after a second it will restarted. I am using a i5 processor with Intel 85bl board. is there anything with eufi bootting.

---

### Post by grahammechanical on 2013-11-07
I know nothing about UEFI boot systems but my BIOS boot system has a setting called Restore on AC power loss. If set to Power Off, then the system goes into the off state after an AC power loss. If set to Power On, then the system goes on after an AC power loss. If set to Last State, then the system goes into either the Off or the On state, whatever the system state was before the AC power loss.

I guess that if it was set to anything other than Power Off, then my machine would reboot when I pushed the power button or clicked shutdown in Ubuntu. Something similar may be happening on your machine.

Regards.

---

