---
title: "Problems with new server access...."
date: 2017-09-07
forum: New to Ubuntu
---

### Post by vgledhill on 2017-09-07
Hi People.

I have followed the tutorial here.... 
[https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-16-04)

Installed the whole stack.... lot of work, and frustration because my iMac is behind me, and when on the server screen... but anyway, enough of my bitching... 

Everything worked.  My server said it was at 192.168.0.25 when I typed in the following command as given in the tutorial
```
[COLOR=#3A3A3A][FONT=monospace]ip addr show eth0 | grep inet | awk '{ print $2; }' | sed 's/\/.*$//'[/FONT][/COLOR]
```

Now when I try to view my server from the mac on the local network I simply get a site can't be reached message... 

Edit.... 

I've just gone to restart apache with the following code and I get the following error.
```
[COLOR=#3A3A3A][FONT=monospace]sudo systemctl restart apache2[/FONT][/COLOR]
```
Job for apache2 service failed because the control process exited with error code.  See "systemctl status apache2.service" and "journalctl -xe" for details.

Please help, I don't know what to do next.   Thanks in advance.

Vince.

---

### Post by vgledhill on 2017-09-07
Solved.... I mistyped AllowOverride All in the phpmyadmin.conf file

---

