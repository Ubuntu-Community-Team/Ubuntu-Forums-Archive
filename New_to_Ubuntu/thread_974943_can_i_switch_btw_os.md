---
title: "can i switch btw os"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by seyiisq on 2008-11-08
I have window xp and ubuntu sitting in different hard drive on my computer. The xp resides on the master while ubuntu resides on the slave. often times i want to work on ubuntu but windows will always come up bcos it is master. pls can someone tell me how to switch from these os.
thanks

---

### Post by hey_ram on 2008-11-08
sure you can switch between different operating systems on your systems...

these types of softwares are known as virutalization programs.

try out virtualBox - that is the open source version.

if you like paying for the stuff that you install and use, you can try out VMWare...

they are more or less the same but each of them  requires a very heavy amount of RAM. the minimum required amount is 512MB RAM, but your system is just going to get stuck up if you run it with the minimal amount. so i would not recommend using it on any system with less than 1 GB RAM.

as for virtualBox, you can install it using the sudo apt-get install virtualBox shell command, or synaptic.

you can also try this thread 
[http://ubuntuforums.org/showthread.php?t=801022](http://ubuntuforums.org/showthread.php?t=801022)

good luck with it!!

---

### Post by kansasnoob on 2008-11-08
Try just installing startupmanager:

```
sudo apt-get install startupmanager
```

It'll then show up in System > Administration > Startup Manager:

[ATTACH]91657[/ATTACH]

As you can see from the screenshot you can select which OS to be the default boot, whether or not to show the bootloader at startup, length of time the bootloader shows before proceeding with the default boot, etc.

---

### Post by crazyness003 on 2008-11-08
I think, from what i read, XP(more acuratly the MBR) dosnt give you th option to boot into Ubuntu. 

Did you install Ubuntu first, then XP? At any rate, take a look at this page:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
or
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

What happend is, XP dosnt like any other OS. So the bootloader that it ships with is very nearsighted. What you basically need to do is install GRUB (**GR**and **U**nified **B**ootloader). This allows you to Boot into Ubuntu, then use a chainloader to get to XP's bootloader to continue into XP whenever you desire.

This is the basic jist of the process:
[hit power button]
[BIOS/CMOS actions take between 3-10 seconds]
[GRUB stage 1.5]
[GRUB Menu.lst shows up]
[Select OS]
...[if XP -> goto XP bootloader]
...[else -> boot Linux Kernel Image]
[Horray]

---

### Post by seyiisq on 2008-11-08
> **crazyness003 said:**
> I think, from what i read, XP(more acuratly the MBR) dosnt give you th option to boot into Ubuntu. 

Did you install Ubuntu first, then XP? At any rate, take a look at this page:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
or
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

What happend is, XP dosnt like any other OS. So the bootloader that it ships with is very nearsighted. What you basically need to do is install GRUB (**GR**and **U**nified **B**ootloader). This allows you to Boot into Ubuntu, then use a chainloader to get to XP's bootloader to continue into XP whenever you desire.

This is the basic jist of the process:
[hit power button]
[BIOS/CMOS actions take between 3-10 seconds]
[GRUB stage 1.5]
[GRUB Menu.lst shows up]
[Select OS]
...[if XP -> goto XP bootloader]
...[else -> boot Linux Kernel Image]
[Horray]

I am not dual booting my os. i have them on seperate hard drive. xp on the master while ubuntu sits on the slaves hard drive.

---

### Post by ugm6hr on 2008-11-08
> **seyiisq said:**
> I am not dual booting my os. i have them on seperate hard drive. xp on the master while ubuntu sits on the slaves hard drive.

This is still strictly a dual-boot situation.

Just enter your BIOS, and select the Ubuntu HD as 1st boot device.

It should (in theory) offer you the option to boot Windows too.

PS: If I read your situation correctly, you have never booted into Ubuntu before.  Who advised you on the installation process, out of interest?

---

