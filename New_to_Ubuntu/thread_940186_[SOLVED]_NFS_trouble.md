---
title: "[SOLVED] NFS trouble"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by lmlypfan on 2008-10-06
I'm mounting a remote folder to my desktop.

nano /etc/exports

/home/bo/servershare/ 192.168.1.135/24(rw,no_root_squash,async)

on the remote machine

sudo mount 192.168.1.145:/home/bo/servershare/ /home/bo/Desktop/servershare/

Every time i go to mount the remote folder with the above command, the remote folder shows up on both the desktop and within the servershare folder i created. 

I've working on this for days, please help

---

### Post by matt1988 on 2008-10-06
The folder showing up on your desktop is just a link to the folder you created. Ubuntu just puts it there when it gets mounted, the same way it puts a link to a flash drive when you insert one.

You can shut it off, but I couldn't tell you where it is as I am not running gnome right now.

Hope that helps :).

---

### Post by lmlypfan on 2008-10-06
That was it. Duh.

Thanks

---

