---
title: "black screen on startup"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by melrokz on 2008-07-02
[FONT="Comic Sans MS"][SIZE="4"]Hi! I'm Melvin from India. I've got a problem whenever i try 2 login 2 ubuntu 7.10. it shows just a black screen. 'failsafe gnome' does not work - it gives the same result. Only after restarting several times am i able to successfully enter the desktop. Plz help me out, I'm a person who has worked on windows till this year.In case there is software 2 install, may i know the package names? or what could this be?[/SIZE][/FONT]

---

### Post by anderskitson on 2008-07-02
The only thing I can think of it's a graphics issue, choose recovery mode at bootup and enter this
> sudo dpkg-reconfigure xserver-xorg
and follow the wizard
then reboot
this will reset your xorg to what you want, if it doesn't work I would try it again with different resolutions and memory.
What are the specs on the machine?

---

### Post by melrokz on 2008-07-02
the graphics card shows up as:
Intel corporation
82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface

---

### Post by anderskitson on 2008-07-02
A issue I had with this same card was with memory allocation in the bios. I would  go into the bios and allow as much memory as possible to that card. and when you are going through the command I wrote above, enter minimum 32768 memory and as much as 65535 . These seemed to fix my problem.

---

