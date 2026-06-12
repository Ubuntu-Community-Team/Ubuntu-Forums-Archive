---
title: "[SOLVED] Shutting Down the Graphical Server"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by drakeman007 on 2008-10-28
Hello!
Just want to know why in ubuntu i dont know other distros, when i install certains updates it ask me for restart my computer, what if my computer is a server and it cannot be restarted to much? there is away to shutdown the X server without stopping al the server services?> and then start up the gui...? it has the same effect ? or really i have to restart all the system?

thanks in advance!
Regards!

---

### Post by Sarmacid on 2008-10-28
When the system asks for a restart it's usually(if not always) a kernel upgrade, and it's something that cannot be done on the fly. To restart the graphic environment just press ctrl + alt + backspace, but it won't do anything if it was a kernel upgrade. You don't really have to reboot after one, but it's the recommended thing to do. You can even set it to automatically do it at the time it's most suitable for you.

---

### Post by drakeman007 on 2008-10-28
> **Sarmacid said:**
> When the system asks for a restart it's usually(if not always) a kernel upgrade, and it's something that cannot be done on the fly. To restart the graphic environment just press ctrl + alt + backspace, but it won't do anything if it was a kernel upgrade. You don't really have to reboot after one, but it's the recommended thing to do. You can even set it to automatically do it at the time it's most suitable for you.

Thanks Sarmacid!
Ok, i  undestand, and what if i want to do it through command line and for example i want to kill the gui and open it again but when i want to open it, there is a way to do it?
Thanks!

---

### Post by Nepherte on 2008-10-28
To stop:
```
sudo /etc/init.d/gdm stop
```

To start it again, simply replace "stop" with "start".

---

### Post by drakeman007 on 2008-10-28
> **Nepherte said:**
> To stop:
```
sudo /etc/init.d/gdm stop
```

To start it again, simply replace "stop" with "start".

Awesome, great, thanks for this help! before i was trying with sudo gdm stop, but with different results it restarts automatically but with this it remains down until i give the start command!
Thanks:guitar:

---

