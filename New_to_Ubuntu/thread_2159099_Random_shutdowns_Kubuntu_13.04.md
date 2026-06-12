---
title: "Random shutdowns Kubuntu 13.04"
date: 2013-07-01
forum: New to Ubuntu
---

### Post by f578652 on 2013-07-01
Hello!

I am new to Linux. I have installed Kubuntu 13.04 (64x) on new Lenovo G580 (Core i5-3230M 2.6 G, 4 GB RAM, Nvidia GeForce GT 635M). But from time to time happen sudden shutdowns as if I forcibly switch off computer holding power button.

I checked the tempratures:
1) Adapter: Virtual device +56C (crit = +127C)
2) Adapter: PCI adapter +53C (high = +95C, crit = +105C)
3) Adapter: ISA adapter
Physical id 0: +56C (high = +87C, crit = +105C)
Core 0: +55C (high = +87C, crit = +105C)
Core 1: +56C (high = +87C, crit = +105C)

As I see these sudden shutdowns don't happen because of the overheating (new laptop without dust inside).

I also tried to find something in syslog file, but I didn't notice anything that says about forced shutdown.

I have reinstalled the system 3 times already, updated and upgraded. But this doesn't help. I searched the wed and forum for resolving this problem but couldn't find anything.
 Also just right now the computer shut down without any running programms on it.

Please help me :-)

---

### Post by SeijiSensei on 2013-07-01
My daughter has a Y570 with an outboard NVIDIA card.  There is a physical switch on her machine that will force it to use the NVIDIA card.  She flips the switch to play games.

I cannot tell from looking quickly at the [specs page](http://shop.lenovo.com/us/en/laptops/essential/g-series/g580/index.html#techspecs) for your machine.  But if you find you have the same switch she does, then shutdown your machine, flip the switch, and reboot into Kubuntu.  Now try running the Additional Drivers command.  It should find the correct NVIDIA drivers and install them.

If you don't have the switch then you may want to look into the [Bumblebee Project]("http://bumblebee-project.org/").

Or the computer itself could be bad.  Try running memtest off the installation disk to check your memory. Do you have a Windows installation as well?  Does the computer work flawlessly in Windows?

---

