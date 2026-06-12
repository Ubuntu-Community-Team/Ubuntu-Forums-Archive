---
title: "[SOLVED] How do you uninstall a program?"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by suomalainen on 2008-11-29
Ubunteros,

I have Skype installed but when I go to the Synaptic Package Manager to remove it, I'm not offered this option. Only install is available.

This leads me to believe I installed it some other way. How can I remove Skype Because I would like to re-install it using the Synaptic Package Manage.

thanks

---

### Post by eternalnewbee on 2008-11-29
Have you looked in **Add/Remove Applications**?

---

### Post by suomalainen on 2008-11-29
Yep! not there.

---

### Post by cdtech on 2008-11-29
Try this, open a termial and type:
```
sudo apt-get remove --purge skype
```

---

### Post by ramaswamyps on 2008-11-29
aptitude autoremove skype
look for what are other packages it will remove before saying yes.

---

### Post by suomalainen on 2008-11-29
Hello,

I tried the Terminal command:

sudo apt-get remove --purge skype

And received the following;

pa@pa-desktop:~$ sudo apt-get remove --purge skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
pa@pa-desktop:~$ 

I don't know how the error message can state that "Package skype is not installed' Because when you look at the attached pic you can clearly see that it is!

---

### Post by suomalainen on 2008-11-29
Hi,

I found the right code to use to remove Skype.

It is:

sudo dpkg -r skype

---

