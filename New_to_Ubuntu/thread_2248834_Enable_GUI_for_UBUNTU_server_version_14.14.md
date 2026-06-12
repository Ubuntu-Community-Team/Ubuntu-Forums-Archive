---
title: "Enable GUI for UBUNTU server version 14.14"
date: 2014-10-17
forum: New to Ubuntu
---

### Post by Laljeev_M on 2014-10-17
Hi

I'm new to Ubuntu / Linux. We have downloaded CD (one CD) for UBUNTU server 14.04. We are using Hyper V 2012 R2 and installing in virtualized environment. Now my question is - is there a way to add GUI to server version, while installing the server we selected GNOME, but end up with errors. Now we prepared the server w/o GUI

Looking for your help

Thanks in advance

---

### Post by nerdtron on 2014-10-17
What errors? What packages did you installed for gnome?

HHmmm you can install the Desktop version of Ubuntu instead and just install the server packages that you need.

Anyway why do you need a gui for? Is there any application that you may need to have a GUI on the server? Everything can be done on the command line (and also easier for remote access).

---

### Post by JDorfler on 2014-10-17
```
sudo apt-get install ubuntu-gnome-desktop
```

Good luck.

---

### Post by ibjsb4 on 2014-10-17
Is gnome really what you want?
[http://packages.ubuntu.com/trusty/gnome](http://packages.ubuntu.com/trusty/gnome)

Or do you want a server gui?
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9)

---

### Post by Laljeev_M on 2014-10-18
Thanks everyone, since I'm a new to Linux it's difficult to manage day-to-day admin activities through command line. That's why planned to add GNOME (specifically speaking adding GUI to server). While added the package GNOME during the installation it shows many errors (we are using the image downloaded / a single CD) , exactly not remembering the error messages, so later we did the basic installation. It will better if we have the GUI - say changing the IP details through cmd end up with error  - after changing the IP address we started the service - [FONT=Ubuntu Mono]sudo service networking restart[/FONT], but end up with error  saying "j[FONT=Ubuntu Mono]ob failed while stopping[/FONT]"

---

