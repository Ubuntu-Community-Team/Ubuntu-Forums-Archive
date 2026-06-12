---
title: "Is it possible to install Ubuntu server directly into Linux Ubuntu 14.04?"
date: 2015-03-15
forum: New to Ubuntu
---

### Post by Evgeny_Rogozin on 2015-03-15
Is it possible to install Ubuntu server directly into Linux Ubuntu 14.04 LTS without installing a virtual environment such as VirtualBox? I ask because see in the Software center servers which can be installed.

---

### Post by dino99 on 2015-03-16
ubuntu server is not an app, it is a different system; so test it in vm or hard install

---

### Post by mastablasta on 2015-03-16
> **Evgeny_Rogozin said:**
> Is it possible to install Ubuntu server directly into Linux Ubuntu 14.04 LTS without installing a virtual environment such as VirtualBox? I ask because see in the Software center servers which can be installed.

yes it can be. Ubutnu server is collection of various server applications. you can install those individually into desktop or more together in stacks (e.g. LAMP stack). a useful application that will help install stacks is tasksel: 
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

note - it is used only for installing.

if you have enough ram a better way is really to use virtual environment such as virtualbox. installation there is not even necessary providing you download the virtual image (for example those found at Bitnami stacks).  

however if you would like to install into virtualbox for example here is an easy guide: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
the guide describes windows but procedure is the same for Linux.

you can also use minimal install iso and then only install things you need. 

if you want your own server with desktop then Zentyal comes with such interface. They also have web GUI interface (where one connects to server via browser).

really it all depends what you want to do. and what is your goal.

---

### Post by coldraven on 2015-03-16
I disagree with 9d9. AFAIK all you have to do is install tasksel (this is the easy way, you could install each component of LAMP separately).
```
sudo apt-get install tasksel
```
then run tasksel
```
sudo tasksel
```
Then use the arrow key to scroll down to Install LAMP server and press the space bar to select it.
After it's installed you should be able to access the server with your browser or a terminal. I cannot remember the IP address, Google it.
There are security issues for running a server with a GUI if you plan to connect it to the internet. So backup your important stuff if this is your main machine.

See: [https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

