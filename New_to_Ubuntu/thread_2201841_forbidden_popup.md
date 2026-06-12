---
title: "forbidden popup"
date: 2014-01-26
forum: New to Ubuntu
---

### Post by adinel_ucv on 2014-01-26
Hi,
A pop-up appears form time to time like the one in the picture, if I watch a movie it jumps back a few seconds... Same thing happens if I run the live cd
What could be the problem?
[IMG]http://imagizer.imageshack.us/v2/800x600q90/35/euu8.png[/IMG]

---

### Post by ibjsb4 on 2014-01-26
Never seen that one.  What media player are you running?  Maybe try a different one.

---

### Post by adinel_ucv on 2014-01-26
I don[COLOR=#444444][FONT=arial]'t think is the player because I get that popup without any opened aplications [/FONT][/COLOR]

---

### Post by ibjsb4 on 2014-01-26
Weird ..

Got restricted-extras installed?

And what exactly are you running?

[https://apps.ubuntu.com/cat/applications/ubuntu-restricted-extras/](https://apps.ubuntu.com/cat/applications/ubuntu-restricted-extras/)

---

### Post by adinel_ucv on 2014-01-26
I use a fresh Ubuntu 12.04 LTS, the only apps I installed are chrome and gimp. Restricted-extras is not installed

---

### Post by ibjsb4 on 2014-01-26
Run this command in terminal and post any errors.

```
sudo apt-get install ubuntu-restricted-extras && sudo apt-get update && sudo apt-get upgrade && sudo reboot
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by adinel_ucv on 2014-01-27
I installed restricted-extras, no errors occurred.

---

### Post by ibjsb4 on 2014-01-28
What kind of graphic card are you running?

```
sudo lshw -c display
```

---

### Post by newb85 on 2014-01-28
I've seen that someone's when I hit the media buttons on my keyboard and there's no application open that receives signals from those buttons.   Does your machine/keyboard have such buttons, and is it possible there malfunctioning?

---

### Post by adinel_ucv on 2014-02-01
I use an Asus EAH3650 TOP.

```
 ~$ sudo lshw -c display
  *-display               
       description: VGA compatible controller
       product: RV630 [Radeon HD 3600 Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:45 memory:d0000000-dfffffff memory:fdde0000-fddeffff ioport:ce00(size=256) memory:fdd00000-fdd1ffff

```

---

### Post by adinel_ucv on 2014-02-01
> **newb85 said:**
> I've seen that someone's when I hit the media buttons on my keyboard and there's no application open that receives signals from those buttons.   Does your machine/keyboard have such buttons, and is it possible there malfunctioning?
I hava a standard keyboard and it works fine, I tried with other keyboards and same thing happens.

---

### Post by ibjsb4 on 2014-02-07
Sorry for the late reply, been out of town.

If you are still trying to resolve this I looked into drivers and found that depending on your card (PCIE or AGP), there are optional drivers available.

[http://support.amd.com/en-us/download](http://support.amd.com/en-us/download)

I do not know if this is a solution.  I do no run radeon, but a possibility.

You can also try upgrading your kernel.

```
sudo apt-get dist-upgrade
```

---

