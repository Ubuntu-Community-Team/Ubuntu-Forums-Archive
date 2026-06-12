---
title: "ubuntu 12.04.5 LTS tty1"
date: 2014-09-16
forum: New to Ubuntu
---

### Post by mahshid2 on 2014-09-16
i want login in ubuntu but come a black page such as terminal 
and ask me username and password  
after that , come this :
welcome to ubuntu 12.04.5 LTS
 how to fix theme and login in ubuntu??
please help me

---

### Post by milos-rajsic on 2014-09-16
to be able to guess what is the problem. Pls try```
 **sudo service lightdm start**
``` to see if the desktop is going to start or will throw some errors.

---

### Post by mahshid2 on 2014-09-17
i try this and restart after it
but don't work :(
this message show 
> 
lightdm start/running , process 1823

please help me again :(

---

### Post by mahshid2 on 2014-09-17
in boot windows by grub (when window not start) come this error :

> 
Error : no such device DC4A57DC4A57B1CE


this can help you ???

---

### Post by milos-rajsic on 2014-09-18
When you proceed with ```
sudo service lightdm start
```
you should try pressing ctrl-alt-F5 or ctrl-alt-F7 to check if desktop is showing anything.

If nothing is happening this is the path to follow:

1) It might be possible that you have interrupted upgrade/update process. Try ```
sudo apt-get update && sudo apt-get upgrade
```. 

2) It might be possible that you did not install graphics drivers properly. In that case installation depends on the graphics card type.

3) Anyway ```
dmesg
``` command might help to see what is the problem as well as ```
sudo lshw
```

---

### Post by sandyd on 2014-09-18
> **mahshid2 said:**
> i want login in ubuntu but come a black page such as terminal 
and ask me username and password  
after that , come this :
welcome to ubuntu 12.04.5 LTS
 how to fix theme and login in ubuntu??
please help me

Hi, what computer are you using? (Manufacturer, model)

---

