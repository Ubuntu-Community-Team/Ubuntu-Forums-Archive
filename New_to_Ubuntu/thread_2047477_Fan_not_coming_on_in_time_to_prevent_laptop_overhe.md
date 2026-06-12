---
title: "Fan not coming on in time to prevent laptop overheating"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by ub07 on 2012-08-25
I am running Ubuntu on a Toshiba Satellite L355D, and I am still having a problem with overheating. I believe that I have traced a possible cause to fan control. It appears that the fan only spins up if there is a sharp increase in temperature. If the temperature increases slowly, the fan seems not to react or to react unreliably.

I downloaded the acpitool for Toshiba, and it is telling me to make sure that I have ACPI support in the kernel enabled. How do I go about doing that?

---

### Post by deadflowr on 2012-08-25
That seems like a bad fan. A fan should start running when the temp hits a certain point, regardless of whether it happens gradually or instantaneous.

---

### Post by ub07 on 2012-08-25
> **deadflowr said:**
> That seems like a bad fan. A fan should start running when the temp hits a certain point, regardless of whether it happens gradually or instantaneous.

I'm beginning to think it's hardware too, but just wondering if there is anything else I can do OS-wise. It overheated a couple of times with Windows, and I opened it up and it was stuffed with lint. I cleaned it out and re-seated the heat sink with new thermal paste. Now it is clean and still it overheats with Ubuntu. I'm testing another OS on a different partition, and the fan behaves differently than with Ubuntu (fan runs less on Ubuntu despite being hot). However, I can't give up Ubuntu because certain software that I use is not available for the other distribution and because I have spent so much time updating and customizing Ubuntu that there is no way that I would give it up now. I just would like to solve this overheating issue because right now the system is not stable.

Yesterday, the CPU temperature climbed to 96 degrees C without the fan coming on. I shut it down because it will turn itself off at 100 degrees C.

EDIT: I do use Jupiter.

---

### Post by sandyd on 2012-08-25
Have you tried using fancontrol to force the fan to spin up at a certain temp?

---

### Post by ub07 on 2012-08-25
> **sandyd said:**
> Have you tried using fancontrol to force the fan to spin up at a certain temp?

I haven't tried fancontrol. I believe that I read a dire warning about it written by the author something to the effect that you can burn out your system using it, but right now I'm desperate and I will try anything. Thanks for the idea.

---

### Post by Toz on 2012-08-25
Toshiba laptops appear to have buggy acpi implementations for Linux-based distros. You could try the following kernel parameters to see if you can "convince" the bios to enable all functionality for non-windows-based OSes:

- **acpi_osi=**
- **acpi_osi=Linux**
- **acpi_osi="Linux"**
- **acpi_osi=\"Linux\"**
- **acpi_osi=\\\"Linux\\\"**

Try all the combinations one at a time to see if they work. Add the value to the GRUB_CMDLINE_LINUX="" line in /etc/default/grub and run:
```
sudo update-grub
```
...and reboot.

And also, if you have an ATI or nvidia graphics card, make sure you install the proprietary drivers.

---

