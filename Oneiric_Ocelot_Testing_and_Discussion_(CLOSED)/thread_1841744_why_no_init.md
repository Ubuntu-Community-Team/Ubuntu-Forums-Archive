---
title: "why no init * ?"
date: 2011-09-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Yeeha on 2011-09-10
with init 3 its very simple to shutdown xserver, now you have to know different commands for different desktops with gdm, kdm stop and so on. How to stop Xubuntu?

---

### Post by fdrake on 2011-09-10
> **Yeeha said:**
> with init 3 its very simple to shutdown server, now you have to know different commands for different desktops with gdm, kdm stop and so on. **How to stop Xubuntu**?

you mean how to shutdown the system?
init is not a good way to stop a program since it kills it. You should try ```
sudo /path/of/running/program stop
```
like: sudo /etc/init.d/apache2 stop

---

### Post by Yeeha on 2011-09-10
There was typo, i meant xserver. I need it to properly generate xorg.conf with xorg -configure. Due to monitor being widescreen and resolution changes on boot and desktop monitor scrolls itself out of range. So i must set monitor info and/or set default resolution 4:3 resolution. Init command under ubuntu dont work anymore and i dont know how to shutdown xubuntu desktop.

---

### Post by fdrake on 2011-09-10
> **Yeeha said:**
> There was typo, i meant xserver. I need it to properly generate xorg.conf with xorg -configure. Due to monitor being widescreen and resolution changes on boot and desktop monitor scrolls itself out of range. So i must set monitor info and/or set default resolution 4:3 resolution. Init command under ubuntu dont work anymore and i dont know how to shutdown xubuntu desktop.

what version are you running. I know that 10.4 (LTS) still has it.

what about 

```
sudo shutdown now

sudo reboot now
```

---

### Post by RomeReactor on 2011-09-10
> **fdrake said:**
> what version are you running. I know that 10.4 (LTS) still has it.

what about 

```
sudo shutdown now

sudo reboot now
```

He only wants to stop the X server, not the whole system.

EDIT: Looking at xubuntu-desktop in Synaptic, it uses LightDM, so to shut down the Xubuntu desktop (once it's running) you'd do:
```
sudo service lightdm stop
```

I think previous versions used GDM, though.

---

### Post by Yeeha on 2011-09-12
Thx, though even setting refresh rates and modelines didnt help. Still low resolutions on boot make monitor go out of range when computer boots 2-3 times.

---

