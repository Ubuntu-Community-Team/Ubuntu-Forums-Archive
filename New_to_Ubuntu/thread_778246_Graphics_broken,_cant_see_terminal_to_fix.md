---
title: "Graphics broken, cant see terminal to fix"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by leotemp on 2008-05-01
So ive been basing my head against getting my second monitor to work since yesterday morning, even though its beyond me i started editing my xorg.conf as none of guis seem to work correctly in regards to screen resolution, now unbuntu boots up and the screen is all over the place and i cant make out enough to use the term and change the file. This is so frustrating im about to just go back to Vista so i can actually use the expensive monitors i own. I dont understand how emulating windows works so well but just changing the rez on a monitor requires backflips through hoops of fire.

Is there a fallback term only way i can boot so i can fix this problem?

---

### Post by xzero1 on 2008-05-01
If you boot in recovery mode (non graphical) from the grub menu, you should be able to at least attempt to fix your problems. Another option is use Ubuntu Feisty Fawn. IMHO, hardy has tried to be too automatic in configuring all possible graphics adapters/displays. With Feisty, at least you can more easily modify xorg.conf to your configuration.

---

### Post by yochaigal on 2008-05-01
-edit-  
I should mention that to access the terminal in non-gui mode you should hit ctrl+alt+F1
This will open a true terminal emulator, so that you can do the following....
to restart X hit ctrl+alt+backspace
to return to gui mode (without restarting X) hit ctrl+alt+F7)
------

If your X window used to work correctly, then there should be a backup xorg.conf file in /etc/X11/.
usually it's called xorg.conf.(whatever date edited it).
an example would be xorg.conf.200710131253

so to restore an earlier xorg.conf, try 

sudo cp /etc/X11/xorg.conf(date) /etc/X11/xorg.conf

This will overwrite your old file.  

Also, if you load xorg.conf.backup, then restart X (ctrl+alt+backspace) then you'll be prompted with the bulletproofX display configuration tool.
if you need to run it from terminal then it's 
sudo displayconfig-gtk

---

