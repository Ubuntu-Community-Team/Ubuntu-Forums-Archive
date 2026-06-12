---
title: "Configure the logoff button."
date: 2008-06-07
forum: New to Ubuntu
---

### Post by crf on 2008-06-07
How do you configure the commands that come up when you click the logoff button?
Are there configuration files?

I am using apm, and not acpi.
I can click a button on the keyboard to suspend to disk, and use the command apm --suspend. But I wish to disable and remove hibernation in the screen that comes up when the logoff button is clicked, and add a suspend to disk option.

---

### Post by crf on 2008-06-09
In configuration editor, I have the key gnome-power-manager : general : can suspend
Checked.
also:
 lshal | grep can_suspend
  power_management.can_suspend = false  (bool)
  power_management.can_suspend_hybrid = false  (bool)
  power_management.can_suspend_to_disk = true  (bool)
  power_management.can_suspend_to_ram = false  (bool)
gconftool-2 -R /apps/gnome-power-manager | grep can
  can_hibernate = false
  can_suspend = true

Shouldn't I have a suspend to disk option when I click the logoff button?
See [http://live.gnome.org/GnomePowerManager/FAQ](http://live.gnome.org/GnomePowerManager/FAQ)

---

