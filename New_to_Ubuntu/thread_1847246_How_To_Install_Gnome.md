---
title: "How To Install Gnome?"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by TemhAAhmeT on 2011-09-20
Hello,

I read this forum and lots of other forums about installing gnome on Ubuntu 11.04. But my problem is regular commands do not work on my ubuntu. I am connecting my vps via ssh and lots of commands do not work. I installed vnc and webmin but while i am instlling gnome commands doesnt works.

And i reinstalled ubuntu 11.04 and want to install gnome and connect gnome via vnc.
May be ssh doesnt supports some commands. So how can i connect without ssh. i have root access.

Thanks..

---

### Post by Frogs Hair on 2011-09-20
Hello and Welcome

The 11.04 desktop release runs on Gnome 2.32 and has the option to use Unity or Ubuntu Classic . the option can be found on the session list below greeter box in the login screen . The list is visible after selecting your user name .

Gnome 3 can be installed via PPA , but removes the Gnome 2 options . When 11.10 is released with Gnome 3 , it will make trying the Gnome shell  much easier , and waiting a month may be a better option .

---

### Post by Paqman on 2011-09-20
Connect to your server and:

To install the full Unity/Gnome desktop:
```
sudo apt-get install ubuntu-desktop
```

To install a more lightweight system:
```
sudo apt-get install gnome-core xorg gdm gnome-themes network-manager-gnome indicator-session
```

But the question is: since you've got Webmin already, what are you hoping to gain by installing a graphical desktop on your VPS?

Can you give us an example of one of the commands that didn't work over SSH?

---

### Post by Frogs Hair on 2011-09-20
Excuse me , I didn't know the op meant server .

---

### Post by SimonBishop on 2011-09-20
Does anyone know how to change who I see (Users) at the log in screen while using Gnome 3?  

In other words, I have several users that will log in remotely, but I they will never be logging into the computer physically.  So, when logging in I just want to see my name there and not the other 10 people.  Thanks.

-Simon

---

### Post by BlinkinCat on 2011-09-20
You really should have started your own thread Simon -

---

### Post by Paqman on 2011-09-20
You should start a new thread for your issue Simon, as it's not related to the OP's.

---

### Post by SimonBishop on 2011-09-27
Sorry.  I did start one.  Thanks.

---

