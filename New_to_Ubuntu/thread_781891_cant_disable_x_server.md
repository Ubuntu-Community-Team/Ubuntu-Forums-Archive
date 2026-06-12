---
title: "cant disable x server?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Rifts on 2008-05-04
after i ctrl + alt + f1 and try to install my driver useing sh command i get this error, this is also after i do sudo etc/init.d/gdm stop


ERROR: You appear to be running an X server; please exit X before installing. For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file  '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

how do i disable it

---

### Post by szymon_g on 2008-05-04
to install nvidia's drivers you have to have Xorg turned off.

logon into computer into command line (i dont remember its name on gdm). in kdm pressing alt + n turned off kdm and give you a standard, command-line login

in case, if it will show you message (when you will try to install those drivers from CLI), you may run 

sudo /etc/init.d/gdm stop

---

### Post by Rifts on 2008-05-05
> **szymon_g said:**
> to install nvidia's drivers you have to have Xorg turned off.

logon into computer into command line (i dont remember its name on gdm). in kdm pressing alt + n turned off kdm and give you a standard, command-line login

in case, if it will show you message (when you will try to install those drivers from CLI), you may run 

sudo /etc/init.d/gdm stop


can you please explain this a little better? i tried alt + n and it does nothing

---

### Post by jimv on 2008-05-05
Use Envy

If you're using Hardy, you can just type this in a terminal:

sudo apt-get install envyng-gtk

EnvyNG will show up in Applications>System Tools

---

### Post by Rifts on 2008-05-05
> **jimv said:**
> Use Envy

If you're using Hardy, you can just type this in a terminal:

sudo apt-get install envyng-gtk

EnvyNG will show up in Applications>System Tools


Yah I have tried envy 3 or 4 times and it does not work

---

### Post by jimv on 2008-05-05
Ok, try this.

Press control+alt+f1

Type 'sudo killall gdm'

Try the install

If that doesn't work, try;

ps -a | grep x

If you see anything like x-session or xserver, kill it with 'sudo killall whatevertheprocessnameis'

Try the install again

---

### Post by aktiwers on 2008-05-05
```
sudo /etc/init.d/gdm stop
```

[http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735](http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735)

---

