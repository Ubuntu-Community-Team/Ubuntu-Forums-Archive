---
title: "Reset internet reboot computer"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-05-14
If my router is rebooted I have to shut down the whole computer in order to reconnect to the internet. Others on the same router don't have to do this

I'm sure there's a nice terminal command I can use to tell my machine that the router is now OK, but I'm damned if I can find it.

My system is 
Ubuntu 11.10
uname -a
3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i686 i386 GNU/Linux

---

### Post by roelforg on 2012-05-14
Run:
```

sudo /etc/init.d/networking restart

```
in a terminal when it happens.

---

### Post by Kevin McCready on 2012-05-14
Thanks but didn't work. I got the message:

 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]
Desktop: command not found

---

### Post by papibe on 2012-05-14
> **roelforg said:**
> ```

sudo /etc/init.d/networking restart

```

+1 for a server (or if you removed network-manager)


If you are running the Desktop version:
```
sudo service network-manager restart
```
Regards.

---

### Post by roelforg on 2012-05-14
> **papibe said:**
> +1 for a server (or if you removed network-manager)


If you are running the Desktop version:
```
sudo service network-manager restart
```
Regards.


Oops... though it does tend to work on my desktops...
(hint: I used ubuntu _server_ and put a custom gui on that for my desktops, lean and mean and under 256mb ram usage and i totally forgot about nm)

---

