---
title: "dual core processor"
date: 2011-09-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ray420 on 2011-09-10
I have tried searching and cant find anything but I'm having problems with my atom n550 processor not scaling right. I'm running 11.10 beta but cant find anything saying that its a problem in the beta or not. if I boot with out the AC adapter only 1 of the the CPU cores is detected. I think the hyper threading or whatever it called isn't detected either. if I go to system monitor it only shows cpu1 and if I boot up with it plugged in it shows cpu1,cpu2,cpu3,cpu4 and runs way faster. If I add acpi=off to the grub menu it does the same thing so not sure if something is wrong with acpi or not.

---

### Post by ray420 on 2011-09-10
I have tried searching and cant find anything but I'm having problems with my atom n550 processor not scaling right. I'm running 11.10 beta but cant find anything saying that its a problem in the beta or not. if I boot with out the AC adapter only 1 of the the CPU cores is detected. I think the hyper threading or whatever it called isn't detected either. if I go to system monitor it only shows cpu1 and if I boot up with it plugged in it shows cpu1,cpu2,cpu3,cpu4 and runs way faster. If I add acpi=off to the grub menu it does the same thing so not sure if something is wrong with acpi or not.

---

### Post by JonM33 on 2011-09-10
> **ray420 said:**
> I have tried searching and cant find anything but I'm having problems with my atom n550 processor not scaling right. I'm running 11.10 beta but cant find anything saying that its a problem in the beta or not. if I boot with out the AC adapter only 1 of the the CPU cores is detected. I think the hyper threading or whatever it called isn't detected either. if I go to system monitor it only shows cpu1 and if I boot up with it plugged in it shows cpu1,cpu2,cpu3,cpu4 and runs way faster. If I add acpi=off to the grub menu it does the same thing so not sure if something is wrong with acpi or not.

Check your BIOS. Hyperthreading is software transparent as it's a hardware feature. Even software that "doesn't support it" will see multiple threads as long is the OS is SMP enabled. I know this because Windows 2000 Pro apparently didn't support Hyperthreading but it still saw (and used) the two threads. It even showed so in the Task Manager.

---

### Post by pqwoerituytrueiwoq on 2011-09-10
does [FONT=Courier New]acpi=force[/FONT] do anything?
*Is taking a shot in the dark*
this may be useful
```
acpi=        [HW,ACPI,X86]
                Advanced Configuration and Power Interface
                 Format: { force | off | strict | noirq | rsdt }
                 force -- enable ACPI if default was off
                 off -- disable ACPI if default was on
                 noirq -- do not use ACPI for IRQ routing
                 strict -- Be less tolerant of platforms that are not
                     strictly ACPI specification compliant.
                 rsdt -- prefer RSDT over (default) XSDT
                 copy_dsdt -- copy DSDT to memory
```

---

### Post by oldfred on 2011-09-10
@   	ray420
I just merged your two threads, so you do not get others responding with similar answers in your other thread.
Please do not post duplicate threads.

---

### Post by ray420 on 2011-09-10
sorry didn't realize I posted twice had problems with internet

---

### Post by ray420 on 2011-09-10
acpi=force didnt work sometimes if i boot up without ac adapter and i plug it in after its started the x-windows fails and i get a black screen with a bunch of different messages and the computer locks up but if i start up with the ac adapter plugged in it wont do that. it did that before i ugraded to the beta build. just didnt notice the cpu problem then

---

### Post by ray420 on 2011-09-11
I just found out if I plug,in my charger and hit a alt,ctrl,backspace and log back in with chrager pluged in my processor works fine

---

### Post by ray420 on 2011-09-11
How does cpufreqd interact with acpi would that cause my problem? Can I simply do a complete uninstall of cpufreqd and revert back to before I installed it or does it edit some system files?

---

### Post by nothingspecial on 2011-09-11
Moved to Ubuntu +1 (Oneiric Ocelot)

---

