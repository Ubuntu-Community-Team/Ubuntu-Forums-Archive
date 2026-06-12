---
title: "ppp dialer problem"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by damansandhu on 2008-05-27
hi , i am using ubuntu 8.04 ,i am using dsl and i configured my internet connection via pppd (in which internet is connected via dialer), but now i have to change my username and password of internet connection when i open pppoeconf in terminal then it stucks at scanning device at 100 percent , nothing happens further , i reseted my modem many times but still nothing happens , is there any other way to change my dsl username and password.

---

### Post by damansandhu on 2008-05-27
somebody help plzz

---

### Post by spiderbatdad on 2008-05-27
Try using the wvdial tool. There are also two graphical frontends that use wvdial called gnome-ppp and kppp.
To set up wvdial run these commands in the terminal:
```
sudo wvdialconf
```This writes the initial file.
Then edit the file to enter the phone# you dial out on, username, and password:
```
gksu gedit /etc/wvdial.conf
```make sure there are no semicolons, or extra charcters at the beginning of the phone, username, password lines. Save the file. Now run:
```
sudo wvdial
```if all goes well, you will connect and be able to open your browser.

---

### Post by damansandhu on 2008-05-27
thanks dude problem solves :)

---

