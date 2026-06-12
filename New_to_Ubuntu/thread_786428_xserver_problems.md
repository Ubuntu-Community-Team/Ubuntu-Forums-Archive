---
title: "xserver problems"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by mudcow007 on 2008-05-08
hello all

im a compleate novice to ubuntu by the way!

im trying to install and configure xserver on a feisty machine, its a fresh install of feisty

firstly i ran "sudo apt-get xorg" 

then "sudo apt-get install xserver-xorg" 

then "sudo dpkg-reconfigure xserver-xorg"

now the graphics card is an nvidia 7200gs so i selected the "nv" driver which i guess is the correct one then i just accept all the defaults on the configuration when thats finished if i run "startx" i get a small black dialogue box with a command prompt an the rest of the screen is grey

anyone any ideas?!

thanks

---

### Post by subzero316 on 2008-05-08
Install Envy:
Press ctrl+alt+f1 you will enter the terminal

there,
```
sudo apt-get install envy
```

---

### Post by mudcow007 on 2008-05-08
right...just trying to install envy 

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/
envy_0.8.1-0ubuntu6_all.deb

sudo dpkg -i envy_0.8.1-0ubuntu6_all.deb


```

then enter envy this give you 6 options to configure envy

when i select "install nvidia drivers" it says "your operative system does nto seem to be supported by Envy"

---

### Post by warbread on 2008-05-08
Sudo apt-get install envy?

If you have a newer card, you'll need envyng-gtk, for which you'll need to activate the universe repositories.  You can go into your /etc/apt/sources.list file and uncomment (delete the '#' at the beginning of the line) the universe repositories.  

I'm curious - why are you installing xserver manually?  Fun?

---

### Post by talsemgeest on 2008-05-08
But anyway, shouldn't you upgrade to hardy? It gives you the new xserver...

---

