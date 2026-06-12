---
title: "detect an external modem"
date: 2014-04-15
forum: New to Ubuntu
---

### Post by merlill on 2014-04-15
Today I am attempting to set up an external modem on a Dell Inspiron with Ubuntu 12.04.4 
The Dell does not have a serial port so I am using an adapter [USB]
I did use the modem and the adapter on another computer with Ubuntu OS so it would appear everything is in working order.
The problem I have is getting the gnome dialer to detect the modem. How do I determine what the problem is?
any ideas?
thanks
merle

---

### Post by merlill on 2014-04-16
I am now online. 
The problem was permissions & the solution was adding myself as a member of the dialout group with the following command in terminal:
sudo gpasswd --add *username* dialout

after logging out and back into my account there were no problems. 

merle

---

### Post by Vladlenin5000 on 2014-04-16
Nice :)
And thanks for the info about the solution.

---

