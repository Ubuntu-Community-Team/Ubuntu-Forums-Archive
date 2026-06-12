---
title: "[SOLVED] GUI Trouble"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Jazzy_Jeff on 2008-09-06
Hello, I was messing around with different GUI's and I then removed them. I am not able to get back into gnome. How do I reset the GUI? Thank you in advance.

---

### Post by Cypher on 2008-09-06
Can you boot your installation and does it get you to a text login prompt? If so, login and type
```

sudo apt-get install gnome-desktop

```
Once the installation completes, reboot the machine with "sudo reboot" and you should have your Gnome desktop back..

---

### Post by Jazzy_Jeff on 2008-09-06
I did not uninstall the gnome desktop. I get a message that says No resume image, doing normal boot...

---

### Post by BenAshton24 on 2008-09-06
ye, do what cypher says then type:
> startx

Hope this helps :D

---

### Post by OutOfReach on 2008-09-06
Hmm, well try this:
```
sudo /etc/init.d/gdm restart
```
See if that helps

---

### Post by Jazzy_Jeff on 2008-09-06
> **BenAshton24 said:**
> ye, do what cypher says then type:


Hope this helps :D


Worked perfectly, thank you.

---

