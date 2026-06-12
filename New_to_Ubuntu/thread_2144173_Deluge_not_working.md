---
title: "Deluge not working"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by TheManno1 on 2013-05-11
Using Ubuntu Studo 12.04 64 bit.
My laptop shutdown from over heating and suddenly Deluge does not work 
/usr/share/themes/Adwaita/gtk-2.0/gtkrc:982: error: unexpected identifier `direction', expected character `}'
/usr/share/themes/Adwaita/gtk-2.0/gtkrc:982: error: unexpected identifier `direction', expected character `}'
[ERROR   ] 17:20:40 ipcinterface:156 Deluge restart failed: Couldn't listen on any:/home/john/.config/deluge/ipc/deluge-gtk: Cannot acquire lock.

---

### Post by ranger1021994 on 2013-05-11
Have a look at the deluge directory that you specified.
*/ipc/deluge-gtk
What all files are there ?

---

### Post by TheManno1 on 2013-05-11
deluge-gtk  deluge-gtk.lock

---

### Post by rishiaditya on 2013-05-18
Deluge was working fine for me for the past 2 weeks and now suddenly stopped responding...now when i click on the icon, nothing happens....Transmission just doesn't cut it for me and am not interested in the whiz bang of Vuze....plz assist.

---

### Post by whyisdaskyblue on 2013-07-15
Same issue... it seems deluge does not like being forced to shutdown. when I close it via its gui it works the next time. when I reboot the system and it forces it to shutdown... most of the time deluge is nuked. I have to delete everything to get it working again... which means I lose my torrents :(

---

### Post by whyisdaskyblue on 2013-07-15
Just solved my own problem... delete all files in the IPC directory. After I did that deluge started fine for me.. no issues noticed.

---

### Post by montyx3 on 2014-02-04
> **whyisdaskyblue said:**
> Just solved my own problem... delete all files in the IPC directory. After I did that deluge started fine for me.. no issues noticed.

Thanks a lot, this workaround solved my issue too.

---

### Post by flipoxp on 2014-09-30
¿Hello are like everybody else? I hope very well ;D.
I have the same problem but I loocking for solution this problem. 
The solution is very very simple and easy...
Please check..

> 
[ERROR   ] 22:07:18 ipcinterface:156 Deluge restart failed: Couldn't listen on any:/home/*****/.config/deluge/ipc/deluge-gtk: Cannot acquire lock.
******@******:~$ deluge restart


Deluge will open but if you close the terminal closes deluge also because you are restarting from the terminal. 
Run your normal deluge and then work again.
God day ;) God bless you

---

