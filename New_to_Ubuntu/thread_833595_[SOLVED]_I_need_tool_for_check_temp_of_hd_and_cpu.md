---
title: "[SOLVED] I need tool for check temp of hd and cpu"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by guevara on 2008-06-18
What is the tool for check temp of hd and cpu. How to install that?
Also what temperature's are average ? 
Thank you guys !

---

### Post by philinux on 2008-06-18
I think you need lm-sensors which is in synaptic.

---

### Post by sdennie on 2008-06-18
For CPU temp you should be able to use:

```

acpi -t

```

For disk temp, you can use smartmontools:

```

sudo apt-get install smartmontools
sudo smartctrl --all /dev/sda | grep Temp

```

---

### Post by super_noob on 2008-06-20
i can't do the 'acpi -t' thing

oloan@ubuntunote:~$ sudo acpi -t
     Battery 1: charging, 20%, 01:24:00 until charged
No support for device type: thermal

i was unable to use sensors because it can not be detected. i've run sensors-detect, but when i run sensors again i keeps saying the same thing.

is it possible that my laptop doesn't have any kind of sensors?

btw, i'm using a-note a5438 with gutsy

thx

---

### Post by cariboo on 2008-06-20
You got the thread marked solved, but you really haven't found a solution. I would suggest installing hddtemp it is available in the repositories and you can either install it from the command line of using synaptic.

Jim

---

