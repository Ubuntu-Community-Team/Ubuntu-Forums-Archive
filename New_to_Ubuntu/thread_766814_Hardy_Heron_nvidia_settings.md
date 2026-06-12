---
title: "Hardy Heron nvidia settings"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by aeoliantunes on 2008-04-25
Having just upgraded to Hardy Heron, there's no nvidia-settings and I need to adjust the brightness/gamma settings on my monitor. How can I do that please?

---

### Post by overdrank on 2008-04-25
> **aeoliantunes said:**
> Having just upgraded to Hardy Heron, there's no nvidia-settings and I need to adjust the brightness/gamma settings on my monitor. How can I do that please?

HI and welcome, the nvidia-settings is not included with the drivers and you can install them via synaptic manager or the terminal ```
sudo apt-get install nvidia-settings
``` or you may prefer aptitude in place of apt-get.

---

### Post by fogcat on 2008-04-25
Use synaptic manager...I have used this for many versions...It just works!

You can use CLI as well....but I thought synaptic as a GUI might be easier if you are new.

fogcat:KS

---

### Post by rajeev1204 on 2008-04-25
> **aeoliantunes said:**
> Having just upgraded to Hardy Heron, there's no nvidia-settings and I need to adjust the brightness/gamma settings on my monitor. How can I do that please?



hi

first go to system/administration/hardware drivers and check whether nvidia drivers are enabled.

If yes then in terminal type nvidia-settings.This will open it up.
Its not a separate file to download but is included with the drivers.


If you want to use the settings frequently, u can create a launcher for it.

Right click on panel > add to panel> custom application launcher.


Enjoy .:)

---

### Post by aeoliantunes on 2008-04-28
Thanks very much. I installed nvidia-settings using apt and created a custom application launcher.  Very helpful post.

---

### Post by alienexplorers on 2008-04-28
In your application launcher you should put the start command as:
> gksudo nvidia-settings
this lets you save your configuration to xorg.conf..
Without the gksudo at the begining of the command no settings will be saved.

---

