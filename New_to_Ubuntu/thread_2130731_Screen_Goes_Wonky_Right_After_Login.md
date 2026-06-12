---
title: "Screen Goes Wonky Right After Login"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by thatstheway on 2013-03-30
Just installed Ubuntu 12.10 on a Toshiba Portege R100, a machine that uses the Trident driver. I'm using GDM. Any ideas? Here are some messages I got from the syslog:

gdm-simple-greeter[1339]: Gtk-WARNING: Overriding tab label for notebook.  
[then "last message repeated 4 times"]  
gdm-simple-greeter[1339]: Gtk-CRITICAL: gtk_style_context_set_path: assertion 'priv->widget == NULL' failed  
gdm-simple-greeter[1339]: Gtk-CRITICAL: gtk_style_context_set_path: assertion 'priv->widget == NULL' failed  
gdm-simple-slave[946]: WARNING: Failed to remove slave program access to the display. Trying to proceed.

---

### Post by dabl on 2013-03-30
Please review the "Video" section of the 12.10 [**[color=green]release notes[/color]**](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop).

Use ```
lspci -nnk | grep -A3 VGA
``` to determine the model of your Trident GPU, and post back if you still have questions.

---

### Post by thatstheway on 2013-03-30
Ah, thanks @dabl, should have looked there days ago. I've got a Trident *Cyberblade* driver, so I'll pull back to 12.04: 

"Trident Cyberblade - As the vesa driver doesn't work with this chip-set the only solution is to remain with 12.04."

---

### Post by thatstheway on 2013-03-30
Confirming that 12.04 works, and I'm up and running. Many many thanks, dabl! : ) 

Note, to get this to work I had to download and then update the Trident Cyberblade driver for my (old) machine (a Toshiba Portege R100), and then write a config file for it, described here: [https://wiki.archlinux.org/index.php/Trident](https://wiki.archlinux.org/index.php/Trident)

---

