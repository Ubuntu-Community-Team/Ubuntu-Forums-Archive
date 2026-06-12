---
title: "[SOLVED] apt-get script ?"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by boglio on 2008-10-04
Hi, I want to make a script or something so i don't always have to write in terminal:
```
sudo apt-get install something
```
And just be able to trim it down to:
```
install something
```

Is this possible, and if so how?


Thanks.

---

### Post by EvilDaemon on 2008-10-04
I don't see why one might want a script. You'd have to manually edit the script for each package you want to install, so it almost defeats the purpose.

---

### Post by Elfy on 2008-10-04
I do it with aliases - you can do many things - edit your .bashrc these are mine, I put them where the alias section is

You don't say what version buntu you use - ```
gedit .bashrc
``` for ubuntu, ```
mousepad .bashrc
```for xubuntu and ```
kate .bashrc
``` for kubuntu

> alias install='sudo apt-get install'
alias remove='sudo apt-get remove'
alias autoremove='sudo apt-get autoremove'
alias search='apt-cache search'
alias purge='sudo apt-get purge'
alias boot='cat /boot/grub/menu.lst'
alias source='cat /etc/apt/sources.list'
alias update='sudo apt-get update'
alias nad='nautilus --no-desktop'
alias gnst='gnome-search-tool'


---

### Post by boglio on 2008-10-04
Thank you! this is exactly what I'm looking for!

---

### Post by JohnFH on 2008-10-04
> **EvilDaemon said:**
> I don't see why one might want a script. You'd have to manually edit the script for each package you want to install, so it almost defeats the purpose.

???? huh

Just put this in your .bashrc file and restart the terminal:

alias inst="sudo apt-get install"

EDIT: Too late again.  Sigh ...

---

### Post by christianvaldes on 2008-10-04
I just wrote this script

> 
#!/bin/bash
sudo apt-get install $1


I named the script install

then I changed its permissions
chmod 777 -R install

the script can be executed with ./install

it works!!!

---

### Post by JohnFH on 2008-10-04
> **christianvaldes said:**
> I just wrote this script

I named the script install

then I changed its permissions
chmod 777 -R install

the script can be executed with ./install

it works!!!

That will only work with one program at a time, so
./install prog1 prog2
will install prog1 but not prog2 which is just ignored.

The alias will install both.

---

### Post by christianvaldes on 2008-10-04
> **forestpixie said:**
> I do it with aliases - you can do many things - edit your .bashrc these are mine, I put them where the alias section is

You don't say what version buntu you use - ```
gedit .bashrc
``` for ubuntu, ```
mousepad .bashrc
```for xubuntu and ```
kate .bashrc
``` for kubuntu

Cool
I like this much better than my solution.

---

