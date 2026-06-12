---
title: "installing skype in Kubuntu on AMD 64"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-08-27
I am trying to install Skype on an AMD 64 computer according to the following instructions.

[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

However, I am not having much luck.

I dowloaded the Ubuntu version off of the Skype website and tried entering things into a Konsole but this is what I have gotten.

llan@allanlaptop:~$ sudo apt-get install skype
[sudo] password for allan:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package skype
allan@allanlaptop:~$ cd Documents
allan@allanlaptop:~/Documents$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package skype
allan@allanlaptop:~/Documents$  sudo apt-get install ia32-libs lib32asound2 libasound2-plugins
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
allan@allanlaptop:~/Documents$ cd: sudo apt-get install ia32-libs lib32asound2
bash: cd:: command not found
allan@allanlaptop:~/Documents$

---

### Post by stoneybroke on 2008-08-28
I have installed Skype without any problems on my Amd Athlon 64 bit computer via the Medibuntu repositories so try this from a terminal window enter,

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

then update the files etc.

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

you can then ether install Skype with synaptic or use,

sudo apt-get install skype

You should then find Skype under Applications>Internet

Hope that helps

---

### Post by TPAKTOPUCTA on 2008-11-06
Thanks :) this is works at my pc.

---

### Post by pealpizar on 2009-08-20
Thanks is the easiest way I ever tried to install skype:popcorn:

---

### Post by Don1500 on 2009-08-20
Sorry, didn't read the date.

---

