---
title: "Disable power settings?"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by sydbat on 2013-07-18
Ubuntu 12.04. 3.5 kernel (I installed). Gnome 3 desktop. This is a tower.


I have recently started using a Bluetooth keyboard and mouse. When I connected the keyboard, the laptop power settings icon showed up in the taskbar. While it is good for showing the amount of battery power on the Bluetooth keyboard, it is very annoying because it keeps showing warnings for the entire system...as in the entire system is on battery. This is not the case, as this system is a tower and plugged in at all times.

When I go to Update manager, it tells me to plug in my computer, as this is safer when updating. Again, a tower, not a laptop.

Is there any way to disable or remove the gnome-power-manager? Would this create a problem with stability?

I have never understood why there needs to be a power manager on a desktop computer. I suppose it is just easier to have it installed by default, than to add it after if needed (for a lappy). But you should be able to remove it or disable it.

---

### Post by newb85 on 2013-07-18
Well, gnome-power-manager is a dependency of several things you probably need to keep around (like gnome-control-center and gnome-panel), so removing it is probably not an option.

If it's telling you that your system is running on battery power when it really isn't, I would bet it's an ACPI problem.  Is your BIOS up-to-date?

I haven't tested this, so I don't know the results, but if you go in dconf Editor (you may have to install it) to org.gnome.settings-daemon.plugins.power, there are a lot more options than are available through the normal interface.  One of them is to disable the power-settings plugin.

---

### Post by sydbat on 2013-07-19
> **newb85 said:**
> Well, gnome-power-manager is a dependency of several things you probably need to keep around (like gnome-control-center and gnome-panel), so removing it is probably not an option.

If it's telling you that your system is running on battery power when it really isn't, I would bet it's an ACPI problem.  Is your BIOS up-to-date?

I haven't tested this, so I don't know the results, but if you go in **dconf Editor (you may have to install it) to org.gnome.settings-daemon.plugins.power, there are a lot more options than are available through the normal interface.  One of them is to disable the power-settings plugin.**
That did it! Thank you for the help.

---

### Post by newb85 on 2013-07-20
Glad to hear it worked.

---

