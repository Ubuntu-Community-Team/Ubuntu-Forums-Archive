---
title: "[SOLVED] can't hibernate"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by ercferret18 on 2008-08-07
I am having problems hibernating on ubuntu 8.04.1.

If I use the hibernate button from the quit menu, the screen just goes blank then after a few seconds comes back up. When I type in a terminal, 

```
sudo /etc/acpi/hibernate.sh
```

the same thing happens, but I get the output,

```
ercferret18@raut-pc:~$ sudo /etc/acpi/hibernate.sh
[sudo] password for ercferret18: 
ifdown: interface eth0 not configured
 * Shutting down ALSA...                                                 [ OK ] 
 * Saving the system clock
/etc/acpi/hibernate.sh: line 39: echo: write error: No such device
Laptop mode disabled, not active.
 * Setting the system clock
Ignoring unknown interface eth0=eth0.
 * Setting up ALSA...                                                    [ OK ] 
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.
ercferret18@raut-pc:~$ 

```

By the way, line 39 of the /etc/acpi/hibernate.sh script says,

```
    echo -n "disk" >/sys/power/state
```

anyone know what's wrong?

---

### Post by ercferret18 on 2008-08-07
please?

---

### Post by eightmillion on 2008-08-07
It seems that people with similar problems have had luck with [µswsusp]("http://suspend.sourceforge.net/"). You might try that. Otherwise, I have no idea.

---

### Post by Rui Pais on 2008-08-08
> Laptop mode disabled, not active.

Have you installed laptop-detect and laptop-mode-tools packages?

Have you tried with sudo pm-hibernate?


> FATAL: Module acpi_sbs not found.
may indicate that you are in these situation:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94332](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94332)


Good luck


edit:
btw whats the output of ```
ls /sys/power
```

---

### Post by ercferret18 on 2008-08-08
output of ls /sys/power...

disk  image_size  pm_trace  resume  state

I will try uswsusp and installing thos packages now...

---

### Post by Rui Pais on 2008-08-08
> **ercferret18 said:**
> output of ls /sys/power...

disk  image_size  pm_trace  resume  state


looks ok. Your acpi seems to work normally...

> **ercferret18 said:**
> 
I will try uswsusp and installing thos packages now...

try first the laptop packages. 
If it still fail then give uswusp a try.

Good luck

---

### Post by ercferret18 on 2008-08-08
ok, i found from somewhere that you have to enable swap and make it as big as your ram, so that is what i did, and it went into hibernate fine. but when coming out, instead the computer just does a normal boot and the swap partition is shown in gparted as an unknown partition. what happened now??

---

### Post by misho1721 on 2008-08-08
I had this problem too, the second set of instructions on this page solved it for me.

[http://ubuntuforums.org/showthread.php?t=326487](http://ubuntuforums.org/showthread.php?t=326487)

---

