---
title: "Power Button Options"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Mr. Man on 2008-10-05
When I used to press my power button I got this window that asked me what I wanted to do shut down, log out, restart, all that stuff. After I changed my password I no longer had the option of shutting down my computer. The window is still there it just doesent have the option that lets me turn it off... PLZ help me

---

### Post by cariboo on 2008-10-05
Can you still use sudo? It might be that some how you took yourself out of the admin group. Go to System--Administration-->Users and Groups. Unlock the application double click on your name, click the User Privileges tab and make sure that Administer the system is checked.

Jim

---

### Post by Mr. Man on 2008-10-06
Yup, its checked

---

### Post by Mr. Man on 2008-10-06
Here is a picture i found on the internet thats kinda like what im having trouble with, but mine only has suspend and hibernate. the picture only has hibernate.

[IMG]http://ares.gobien.be:8080/ubuntu/shutdown.jpg[/IMG]

just so that if the image doesent work here is the url (just for sure...
[http://ares.gobien.be:8080/ubuntu/shutdown.jpg](http://ares.gobien.be:8080/ubuntu/shutdown.jpg)

---

### Post by emobrad on 2008-10-06
```
sudo apt-get install gdm
```

You probably got rid of some dependancies you needed for that somehow. Try that and tell us how it goes

---

### Post by Mr. Man on 2008-10-06
I got this...

thijs@thijs-laptop:~$ sudo apt-get install gdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gdm is already the newest version.
The following packages were automatically installed and are no longer required:
  python-zopeinterface menu kdebase-bin-kde3 kicker libempathy-common libawn0
  libkonq4 libfltk1.1 libgavl0 gnustep-common tcl tcl8.4 libgtk1.2-common
  python-setuptools gnustep-back-common python-pkg-resources
  libempathy-gtk-common jackd gstreamer0.10-gnonlin
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
thijs@thijs-laptop:~$

---

### Post by tarps87 on 2008-10-06
I have had this before but can not remember how I solved it, have you got any other users logged on? I think restarting may have fixed it.

Edit: I think to was ```
sudo dpkg-reconfigure gdm
```

---

