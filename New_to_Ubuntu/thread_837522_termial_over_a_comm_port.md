---
title: "termial over a comm port"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by PocketLint on 2008-06-22
I need to connect to an embedded linux box over the comm port from my ubuntu pc.
How do I do that? I'm very new to Linux.

I tried the terminal program in ubantu but that just seems to want to connect to my local machine and I can not find any setting to redirect the input and output over the comm ports.

any help would be great.

-Bob
-

---

### Post by uclalinux on 2008-06-22
I am confused about what you want to do due to my own ignorance of computer vocabulary. But I think you want to connect to a linux terminal from another computer?
If this is so you need to install openssh-server to the server host computer. this can be done by typing  ```
sudo aptitude install openssh-server
```, then from the remote computer goto the terminal and type
```
ssh <user_name>@<ip address>
```, an example would be ```
ssh uclalinux@10.10.10.101
```. Is this what you were looking for?

---

### Post by The Cog on 2008-06-22
Install the package gtkterm. minicom also works but I prefer gtkterm. They are both serial terminal emulators, and should to wht you want. Your COM1 port is probably called ttyS0 in Linux, and I think both those programs will defualt to that port.

---

### Post by PocketLint on 2008-06-22
Thanks to The Cog..

Yup that was what I was looking for and I am now connected. thank you!!

---

