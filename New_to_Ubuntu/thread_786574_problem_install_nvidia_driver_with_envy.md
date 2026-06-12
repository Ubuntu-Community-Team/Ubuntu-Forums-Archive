---
title: "problem install nvidia driver with envy"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by elend_heiler on 2008-05-08
halloo all..:KS

hufff..another problem..
after success solved my login screen resolution..

i don't know how to install nvidia driver..
i already used Envy for installing..but when the process took place..
the error ocured from envy..

like this...

"There was an error in the installation process. You can see the log file /var/log/envy-installer.log"

whats wrong??

thanks before!! :KS

---

### Post by Delever on 2008-05-08
> **elend_heiler said:**
> 
"There was an error in the installation process. You can see the log file /var/log/envy-installer.log"


Open terminal, enter

gedit /var/log/envy-installer.log

and post at least last lines here.

---

### Post by hunterxh on 2009-01-12
this is my log file:
python pulse.py nvidia 
root@ubuntu:/usr/share/envy# python pulse.py nvidia
Envy - Version 0.9.10
ENVY ERROR: Your Operating System does not seem to be supported by Envy

please help me 
i 'm using ubuntu 8.10

---

### Post by cb34 on 2009-01-12
if all else fails, i'd forget about envy or any other helper program and check out my post in this thread.. [http://ubuntuforums.org/showthread.php?p=6538071](http://ubuntuforums.org/showthread.php?p=6538071)

i've installed and uninstalled nvidia drivers many many times testing all kinds of driver versions and things.. it's pretty simple after the first time you do it, and is in reality more predictable and reliable than using any graphic helper program.

basically what i wrote how i do it is how it's written in many places all over this forum, and instructions on nvidia's site on the page you download the driver. you dont need envy, i never used envy, never even seen it or know what it is or how it works, but you dont need it.

hope you get it sorted, exactly what you wanna do is written all over the place, just look for install nvidia driver, and you'll get lots of help and instructions.

if you insist on getting envy to work, than i have no clue.
that's a real weird error message, your OS is not supported ???

---

