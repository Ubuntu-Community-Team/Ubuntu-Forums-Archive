---
title: "ubuntu is leaving fans and leds on after shutting down but windows powers off ok"
date: 2022-04-16
forum: New to Ubuntu
---

### Post by denisernesto4 on 2022-04-16
i have installed ubuntu 20.04.04 in dual boot with windows 10. windows 10 powers off PC correctly but ubuntu  does not, after shut down  the keyboard and monitors turns off but CPU, GPU and case fans still on and case leds lights too. i already installed kernel 5.11.5 and 5.16.20 but nothing changes what could be the cause and solution how could i find a log of my hardware and post here, what i remenber is that my motherboard is an ecs h81h3-m4 socket lga1150 with xeon e3-1231 v3 16gb ram ddr3 , 2x 240 sdd and 3x hdd , gpu is xfx  rx570 4gb

---

### Post by ActionParsnip on 2022-04-17
Does the system have a make and model?
Do you have the latest BIOS?

---

### Post by grahammechanical on 2022-04-17
What happens if you power off using the terminal

```
sudo shutdown --halt now
```

or

```
sudo shutdown --poweroff now
```

Edit: --halt shuts down the operating sytem but does not power off the machine. That has to be done by the on/off switch. Whereas --poweroff shuts down the operating system and powers off the machine.

Regards

---

