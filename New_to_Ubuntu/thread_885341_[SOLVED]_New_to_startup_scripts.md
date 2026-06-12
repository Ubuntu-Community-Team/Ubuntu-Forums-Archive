---
title: "[SOLVED] New to startup scripts"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by VOLKOV9 on 2008-08-10
I have an nVidia card, and I run Ubuntu 8.04 64-bit.  When I run
```
nvidia-settings -a InitialPixmapPlacement=2
nvidia-settings -q InitialPixmapPlacement
```,
I get 2, as I should.  So then I run
```
cd /etc/init.d/
gksudo gedit 2DFix.sh
```
and write
```
#!/bin/sh
nvidia-settings -a InitialPixmapPlacement=2

```, save, and close.  Then I run
```
sudo chmod 777 2DFix.sh
sudo update-rc.d defaults
```.  However, on reboot,
```
nvidia-settings -q InitialPixmapPlacement
``` yields 1.

Can someone point to what I did wrong?

---

### Post by sdennie on 2008-08-10
The nvidia-settings program needs to have an active X session running to work.  Rather than setting IPP=2 in /etc/init.d or /etc/rc.local, I would recommend setting it via a script that you run at startup via System->Preferences->Session.  Also, be careful with that setting as it can cause some stability issues (at least with laptops).

---

