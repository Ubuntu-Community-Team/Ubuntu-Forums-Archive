---
title: "My laptop keeps freezing on UBUNTU login screen"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by TylerWen on 2011-09-19
Hi, I just installed ubuntu earlier today and it was running smoothly for a few hours - I proceeded to shut down my laptop and commute home from school. Once I got home from school I powered up my laptop and it gets to the login screen and as soon as I type one letter it freezes including my mouse. I'm using ubuntu 11.04. 

Please help :( ,

Tyler

---

### Post by josephmills on 2011-09-19
when you get to your login screen press ctrl+alt+f1 then sign in 
then do a ```
sudo /etc/init.d/gdm restart
``` then restart computer.Anything ?

---

### Post by TylerWen on 2011-09-19
it keeps freezing in the middle of typing the code
:(

---

### Post by josephmills on 2011-09-19
try  ctrl+alt+f2  nothing 

just try to get a ```
sudo reboot
``` in there.

when you get the ubuntu plymouth splash press the up button and look for errors or fails. 
anything ?

it will not show your password when typing it in.

---

### Post by TylerWen on 2011-09-19
once i type sudo reboot it asks for a password... my login password?? it always freezes there too - very frustrating

---

### Post by josephmills on 2011-09-19
> **TylerWen said:**
> once i type sudo reboot it asks for a password... my login password?? it always freezes there too - very frustrating
enter login password and hit enter it will not show your password for security reasons but it is working

---

### Post by TylerWen on 2011-09-19
unfortunately wont let me get that far.

---

### Post by TylerWen on 2011-09-19
i switch the boot order to network boot: atheros boot agent first out of desperation... i then did ctrl alt f2 n got to the screen that says 
Ubuntu 11.04 tyler-Aspire-5250 tty2

tyler-Aspire-5250 login: 


I entered: sudo reboot  and then my login password but it said incorrect login - i also tried sudo/etc/init.d/gdm restart
same thing

---

### Post by TylerWen on 2011-09-19
i kept it in the boot order as previously mentioned and just entered my password in the regular login screen.... it works :o

---

