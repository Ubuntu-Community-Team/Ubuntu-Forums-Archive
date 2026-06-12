---
title: "ubuntu NOT asking for password anymore !!"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by blade4 on 2011-11-04
Hi guys , bit of a bind here : for some reason , ubuntu has stopped asking for password on ANYTHING . Synaptic  , update manager , deb file install , heck even sudo-ing in terminal is now password free . While this has made my system more user friendly than ever , I'm concerned about the security ramifications this might have . 

I'm using ubuntu 10.04 . Any help is appreciated .Thanks in advance :)

---

### Post by Carborundum on 2011-11-04
Sounds like you might have accidentally activated the root account, and are using that instead of a regular session.

If you open a terminal, what does the prompt look like? Does it say
```
blade4@blade4-computer:~$
```or
```
root@blade4-computer:~#
```or something else?

(Assuming 'blade4' is your username on your computer, which is named 'blade4-computer')

---

### Post by blade4 on 2011-11-04
The terminal prompt hasn't changed :

 blade4@ubuntu:~$

---

### Post by blade4 on 2011-11-04
sudo gedit /etc/sudoers 

I removed the line 

ALL ALL=(ALL) NOPASSWD:ALL

& everything is fine now.

Thanks for the help anyway Carborundum ,

cheers :)

---

