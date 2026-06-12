---
title: "How do I boot Ubuntu using safe graphics mode?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by Samurai Penguin on 2008-06-25
I need to boot Ubuntu using safe graphics mode. How do I do this once Ubuntu has been installed to the Hard Drive?

---

### Post by luisito on 2008-06-25
I guess that you are not happy booting failsafe as offered in the grub menu.

You can do the following, which is not great (maybe not easy) but it is possible.

Boot failsafe. It will give you a command prompts but no graphics.

Try the command ```
sudo nano /etc/X11/xorg.conf 
```

This will open a text editor with the configuration file for your X Window system. Scroll down until you get to Section "Device". Somewhere it will say
Driver "something". Comment out that line by adding the character '#' at the beginning. Now add a line right below this one that says
Driver "vesa".

Press Ctrl-X to save and quit. Now you should be back at the command prompt where you will type sudo reboot to reboot (or just press Ctrl-Alt-Delete)

Hopefully, if everything works fine, you will reboot in safe graphics mode.

---

### Post by wolfen69 on 2008-06-26
> **luisito said:**
> I guess that you are not happy booting failsafe as offered in the grub menu.



it is only offered if you press esc

---

### Post by Cheesecakeman on 2008-06-26
Well this is relevant to me. 

If I installed in Safe Graphics mode, does that effect the final installation?

If so, anyway to make it so I'm not constantly in safe graphics mode? o.o I'd like to have a resolution higher then 640 x 480

---

