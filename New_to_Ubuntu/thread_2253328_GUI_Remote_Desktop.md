---
title: "GUI Remote Desktop"
date: 2014-11-18
forum: New to Ubuntu
---

### Post by karlowbrian on 2014-11-18
Hello Ubuntu!
I have a rather difficult question that I would like to know is possible and if so, how to do it. I would like to be able to access my personal computer at home running Ubuntu 14.04 from another computer running 14.04. I would prefer that it be a GUI interface instead of text. Is this possible? If so what are the steps I need to take for this to work?

Thanks guys! 
-Brian

---

### Post by Kirk Schnable on 2014-11-19
Hello,

The main two protocols typically used to access a Linux Remote Desktop are VNC and NX. 

VNC typically provides direct remote control over what's on your screen, and NX is typically more like "Microsoft Terminal Services" where you can have multiple sessions and desktops at once. NX is generally more bandwidth efficient than VNC as well.

NX is easy to set up on top of most servers because it works through SSH directly. 

My favorite solution for NX right now is X2Go. 

[http://wiki.x2go.org/doku.php/doc:newtox2go](http://wiki.x2go.org/doku.php/doc:newtox2go)

Best Regards,
Kirk

---

### Post by karlowbrian on 2014-11-19
Thanks Krik Shnodle! I will look into it!

---

### Post by Sef on 2014-11-22
Moved to New to Ubuntu.

---

### Post by sammiev on 2014-11-22
Have a look at [TeamViewer]("http://www.teamviewer.com/en/download/linux.aspx"), very enjoyable and easy to manage.

---

### Post by karlowbrian on 2014-11-23
Okay I will check it out! Thanks!

---

