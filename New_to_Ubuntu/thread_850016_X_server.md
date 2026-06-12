---
title: "X server"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by ub007 on 2008-07-05
I'm trying to install an IDE for python,tried 2 of them -eric and spe.I get the error msg:canot connect to X server

Could anyone tell me whats missing here?

---

### Post by ibutho on 2008-07-05
How did you try to run them? Were you logged into an X session?

---

### Post by ub007 on 2008-07-05
I've got ubuntu installed on VMWare...
steps i followed:  opened terminal
#sudo apt-get install eric
#eric
#eric4    :   py cannot connect to X-server

> Were you logged into an X session?I'm lost there,the answer would be i do not know...

---

### Post by ZabiGG on 2008-07-05
If you are logged into a graphical interface, Gnome, KDE or whatever, that is what is wrong. You will have to install exclusively from a terminal (a tty), and shut down your window manager to be able to perform your installation.

[B]Step 1
[/B]
CRTL-ALT-F1

to switch to the first TTY

[B]Step 2
[/B]
Log in (enter your user name and password as you would on your graphical login page)

**Step 3**

sudo /etc/init.d/gdm stop

to shut down your GUI, if you are using KDE, remplace gdm by kdm

[B]Step 4
[/B]
follow the installation instructions for your application

[B]Step 5
[/B]
sudo /etc/init.d/gdm start

(or kdm start, as applies)

[B]Step 6
[/B]
(type)
exit

[B]Step 7
[/B]
CTRL-ALT-F7

to switch back to your GUI and log on.


Hope this helps,

Z.

---

### Post by ub007 on 2008-07-05
Thanks,will try that out on monday...ctl+alt+f1 doesnt work on vmware....

---

