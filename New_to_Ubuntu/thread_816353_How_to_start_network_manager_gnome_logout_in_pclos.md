---
title: "How to start network manager gnome logout in pclos?"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by bhadotia on 2008-06-02
I have recently switched to pclos (gnome 2008 and 2007) from ubuntu 8.04.
I don't like the default network manager there so I installed the package network manager from synaptics . Now I'm unable to  start  it  from the  CL.
When I give the command  networkmanager the following message comes:
bash: networkmanager: command not found

I googled for the solution , but to no avail.

Need help.

Also I'm unable to find the package which is responsible for the log out splash screen in ubuntu (which contains lock screen log out  shut down etc.)- I don't know what the package is called. Can someone tell me the name of that package . The package is not installed by default in pclos but I like it .

Many thanks in advance.

---

### Post by Inxsible on 2008-06-02
The gnome network manager starts with ```
nm-applet
```You might want to put that in the Alt + F2 Run dialog...so you dont have to keep the terminal open.

I am not sure about the gnome logout, coz I use Xubuntu. but i think it is ```
gnome-logout
``` But wait on it for someone else to confirm.

---

### Post by SunnyRabbiera on 2008-06-02
Eh PClinux itself is a decent distor, but its official forum is full of #@$%&

---

### Post by bhadotia on 2008-06-02
There is no package such as GNOME-logout listed in the synaptics . Also I did not find the package network-manager-gnome , so I installed knetworkmanager as frontend to network manager. Now knetworkmanager says networkmanager is not running. So how can we start net work manager.


I think I had seen the the package gnome-logout in the pclos 2007 ,but I think that was when I had just installed pclos but after its first update(677MB) when the repos were updated ,it was not there. It can also be that am mistaking. I tried some 5 distros in a day so it might be it was somewhere else. Is there any site from where this package be downloaded.

---

### Post by Inxsible on 2008-06-02
Did you try nm-applet for your networking issue? I am sorry... I don't know much about the log out

---

