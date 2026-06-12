---
title: "Edit Terminal"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by linuxland on 2012-08-10
I am new to linux, but have made the transition and installed Ubuntu without much issue, one thing though is as I am trying to install stunnel I found I could not edit a value in a line, it asked me to change  from a "0" to a "1", and it will not allow me?

Please advise.

Thank you in advance!

---

### Post by papibe on 2012-08-10
Hi linuxland. Welcome to the forums ):P

If you want to modify a file that requires administration privileges you need to use sudo or gksudo.

For example, if you want to edit your /etc/resolv.conf to change DNS:
```
sudo nano /etc/resolv.conf
```
That will open a editor inside the terminal. 

If you want to use a GUI editor. Try this:
```
gksudo gedit /etc/resolv.conf
```
I hope these examples point you in the right direction. Let us know how it goes.
Regards.

---

### Post by Gone fishing on 2012-08-10
You were doing this ```
vi /etc/default/stunnel4
```from this tutorial [http://www.ubuntugeek.com/stunnel-universal-ssl-tunnel-for-network-daemons.html](http://www.ubuntugeek.com/stunnel-universal-ssl-tunnel-for-network-daemons.html) ?

I think vi /etc/default/stunnel4 should be sudo vi /etc/default/stunnel4 however if your new to Linux I'd suggest not using vi gedit will be fine ```
gksu gedit /etc/default/stunnel4
```

---

### Post by cortman on 2012-08-10
Vi  == ouch for new user.
If you must use a terminal editor, Ubuntu comes with nano. It's pretty simple and has a handy legend of commands along the bottom.
Vi drove me nuts the first time I used it... the whole modal thing made no sense to someone with no GNU/Linux/Unix background. :)

---

