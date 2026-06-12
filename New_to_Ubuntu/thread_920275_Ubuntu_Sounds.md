---
title: "Ubuntu Sounds"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by icyest on 2008-09-15
Every time I type something, say in Nautilus's directory box, or a text box, I hold backspace a lot. What ends up happening is that if I've already deleted every character, this loud annoying beep noise is made. How do I stop that?

---

### Post by tarps87 on 2008-09-15
Go into system -> preferences -> sound and deselect "enable system beep" from the system beep tab

---

### Post by kabotage on 2008-09-15
You can disable this by editing a file and entering two simple lines.

 gedit /etc/modprobe.d/blacklist


 And then add:


 #silly speaker beep
blacklist pcspkr


 Save your file and the speaker beep will be gone when you reboot.
 If you don&#8217;t want to wait until a reboot, simply type:


 sudo rmmod pcspkr


reposted from [http://www.arsgeek.com/2006/08/23/how-to-turn-off-the-annoying-system-beep-in-linux-debianubuntu/](http://www.arsgeek.com/2006/08/23/how-to-turn-off-the-annoying-system-beep-in-linux-debianubuntu/)

---

### Post by crazypenguin2008 on 2008-09-15
i left mine on because it drives my girlfreinds cat nuts:lolflag:

---

