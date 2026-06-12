---
title: "USB port -- permission denied -- Repetier"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by Rivinski on 2013-04-26
I'm brand new to Ubuntu and I'm trying to install a 3d printer in a program called Repetier.  Whenever I try to connect to the printer using the proper port, I get an error message saying "permission denied".  This error is given by/in the Repetier Host software.  I'm certain that I am choosing the correct port in Repetier, but (I think) Ubuntu is denying Repetier permission to access the usb port.  What do I do?

---

### Post by joeltrane on 2013-06-15
Hello,

Have you seen this?: [Solidoodle On Linux]("http://wiki.solidoodle.com/linux")

- Joeltrane

---

### Post by 3rdalbum on 2013-06-15
Can you change the permissions of the device in the /dev/ folder?

sudo chmod a+rw /dev/(device file)

---

