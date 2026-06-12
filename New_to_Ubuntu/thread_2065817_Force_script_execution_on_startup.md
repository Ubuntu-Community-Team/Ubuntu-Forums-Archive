---
title: "Force script execution on startup"
date: 2012-10-02
forum: New to Ubuntu
---

### Post by phi19 on 2012-10-02
Hi, I'm on Ubuntu 11.10 and due to the fact that my computer does not recognize the Brightness comands on my keyboard, I am forced to use the following command:
```
sudo setpci -s 00:02.0 F4.B=20
```

If I don't execute this, looking at my screen feels like staring at the sun.

So, my question is: how can I force Ubuntu to execute this line on startup?

Thanks!

---

### Post by 2F4U on 2012-10-03
You could put the command in the file /etc/rc.local, so that it will be executed as part of the boot process. Using this method, the script will be executed independent from a user login.

---

### Post by NikTh on 2012-10-03
Yes , rc.local is the best file to include this command. And no need of sudo. 

```
gksudo gedit /etc/rc.local
``` 

and add the command **before exit 0**

```
setpci -s 00:02.0 F4.B=20
``` 

save and reboot. 

If command not executed , then add a little delay 

```
(sleep 2 ; setpci -s 00:02.0 F4.B=20) &
``` 

Thanks

---

