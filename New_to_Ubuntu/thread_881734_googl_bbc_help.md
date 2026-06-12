---
title: "googl bbc help"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by blake7 on 2008-08-06
googl bbc help


hi i have just loaded google earth when i open the it says choise an application.
what do i do next.
please help
also i can not get live vidio from the bbc working if you could help with that too i would be very gratfull.

thank you

ps i have no ider how ubuntu works so please be very detailed thank you

pss why dont you all just make one operating system that works
with out all the rubbish like i keep finding

---

### Post by ibizatunes on 2008-08-06
bbc site you need flash installed to run it, as currently due to DRM protect file, we (linux users) can download them only stream them!

---

### Post by tuxxy on 2008-08-06
Did you install ubunut-restricted-extras package, this will install many codecs and Flash

```
sudo apt-get install ubuntu-restricted-extras
```

If no luck install the flash codec

```
sudo apt-get install fluashplugin-nonfree
```

Youttube atleast should work now, if not check what plugins you have installed by entering about: plugins into browser.

---

### Post by blake7 on 2008-08-08
how do i run somthing ???

---

### Post by blake7 on 2008-08-08
ok i think thjis is what yiou mean

i got this messaage
a@a-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for a: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
a@a-laptop:~$ 
a@a-laptop:~$ 
then i didi that which gave this message
a@a-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
a@a-laptop:~$ 
a@a-laptop:~$ 

what does that mean???

why is this all so ******* pain in the **** caant so one design an os which does not requaire ******* mothering ever too mins

what is the problem?

any if you could help with the problem i wwould be thank full

chhhers

---

### Post by okey666 on 2008-08-08
Super user is an administrator (sort of).

You can run any command with admin privileges by putting
```
sudo
```
before the command.
In your case:
```
sudo dpkg --configure -a
```
 When you use sudo this will happen:
```
oscar@oscar-desktop:~$ sudo gedit
[sudo] password for oscar:
```
(gedit is a text editor)
When you type in your password, no characters will appear, just type it in anyway and press enter.


If you want to install stuff a graphical way, go system>>admin>>synaptic
This is the graphical way of installing specific packages.

---

