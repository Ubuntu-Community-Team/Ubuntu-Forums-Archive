---
title: "an accidental closure while installation"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-08-15
i ran the following in the terminal to install ubuntu restricted extras:
sudo apt-get install ubuntu-restricted-extras

unfortunately,i closed the terminal while it was at work,installing the things.now when i try to open the synaptic,i get the message:
"an error occurred 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."
and i can't install any software using synaptic since it closes giving this message.
i want to uninstall all the restricted extras that i wanted to install.how can i make the system recover?

---

### Post by stonecoldjha on 2008-08-15
yea,one more thing,i also went to the terminal and typed:
dpkg --configure -a
the following was the output


sonu@sonu-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
sonu@sonu-desktop:~$ 

now what does that imply,the only user cum administrator is me.

---

### Post by stonecoldjha on 2008-08-15
please help me out.

---

### Post by Crafty Kisses on 2008-08-15
Run the following:
```
sudo dpkg --configure -a
```
That should work.

---

