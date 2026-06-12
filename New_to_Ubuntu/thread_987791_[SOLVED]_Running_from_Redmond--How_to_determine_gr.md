---
title: "[SOLVED] Running from Redmond--How to determine graphics card?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Montserrat on 2008-11-19
I've just arrived as a Windows refugee. I've installed Google Earth. Now I'd like to upgrade the driver to enhance its performance. I'm doing this on Intrepid 8.10. How do I determine which graphics card I have?

---

### Post by crazyness003 on 2008-11-19
Hello and welcome.

a good way to determine your grfx card is to run this command in the terminal (the 'dos command prompt' of *nux, found in *Applications -> Accessories -> Terminal*). 
```
sudo lshw -class display
```SUDO means super user do, and temporarly enables you to log in and execute a command as the root user. be careful, as this allows 100% access to the system, so make sure you trust the command you're giving (you can trust me tho :))

lshw is the 'list hardware' command built into the temrinal

-class display ~ this tells the lshw to only output 'display information' regrading your hardware.

This is mine
```
crazyness003@crazymachine:~$ sudo lshw -class display

  *-display               
       description: VGA compatible controller
       product: C51 [Geforce 6150 Go]
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

```as you can see i have an nVidia Geforce 6150 Go, running at 66MHz in 64bits.

FYI: To see ALL of your hardware, just issue this command
```
sudo lshw
```This will display ALL of your hardware (even each memory module, i think)

welcome to Ubuntu and i hope you have fun.

---

### Post by Montserrat on 2008-11-20
Thank you Crazyness. I see that I have an SiS M650/740 PCI/AGP VGA Display Adapter. Might need to upgrade it to an nVidia if I'm to get much pleasure out of Google Earth. 

But anyway,the important thing is getting started with Ubuntu.

Thanks again.

---

### Post by crazyness003 on 2008-11-20
> **Montserrat said:**
> Thank you Crazyness. I see that I have an SiS M650/740 PCI/AGP VGA Display Adapter. Might need to upgrade it to an nVidia if I'm to get much pleasure out of Google Earth. 

But anyway,the important thing is getting started with Ubuntu.

Thanks again.

You're welcome. Just make sure you mark your thread as [solved] when it gets solved (or close enough) by using the [COLOR=Red]_**[Thread Tools]("http://ubuntuforums.org/showthread.php?t=987791&nojs=1#goto_threadtools")**_[/COLOR][IMG]http://ubuntuforums.org/images/misc/menu_open.gif[/IMG] in the upper-right area of the page.

Again, welcome and enjoy freedom like never before.

---

