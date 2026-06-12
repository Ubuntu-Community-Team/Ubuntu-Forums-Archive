---
title: "[SOLVED] Couldn't launch application"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by ellalan on 2008-08-19
Hi
I have a problem with this Error notification,

I have installed Cairo-Dock but when I try to launch I get this Error:

Couldn't launch application

Failed to execute child process "/home/user/16484_files/instructions.gif"(Permission denied)
I was playing using nautilus and I believe that I have deleted something by mistake could someone please tell me how to correct this. Thank you.

---

### Post by meanburrito920 on 2008-08-20
how did you try and launch it? Try opening a terminal and typing 

$ sudo cairo-dock

---

### Post by ellalan on 2008-08-20
Hi
I get the warning when I tried to open with $ sudo cairo-dock

warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
cairo_dock_load_gauge (112x112)
warning :  (applet-nvidia.c:cd_nvidia_read_data:62)  
  nVidia : couldn't acquire GPU temperature
 is 'nvidia-settings' installed on your system and its version >= 1.0 ?
warning :  (applet-nvidia.c:cd_nvidia_update_from_data:82)  
  Couldn't get infos from nvidia setting (may not be installed or too old), halt.
^[[3~

---

### Post by ellalan on 2008-08-20
I have solved by removing cairo-dock and the plugins using synaptics and re-installed them. Thanks again.

---

### Post by fabounet on 2008-08-20
launching an app with sudo is rarely a good idea, the config files will belong to root then.

---

### Post by meanburrito920 on 2008-08-20
I suggested it because of the permissions errors, running it as root would have taken care of that.

---

