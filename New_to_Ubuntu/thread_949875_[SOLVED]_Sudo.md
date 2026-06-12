---
title: "[SOLVED] Sudo"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by newkomkommer on 2008-10-16
I tried to install the Ati driver for Ubuntu. You need to use the terminal and the terminal keeps asking me for my Sudo password. I never made a Sudo password and my account password wont work either. Please help me to find the password of or help me change it.

---

### Post by aysiu on 2008-10-16
If you're the first account created during installation, your account password is your *sudo* password.

---

### Post by kodalisrikanth on 2008-10-16
Whenever you want to install any administrative task you need to be a superuser of the system.

But here your password is not working because you are not in the sudoer list. Ask the system admin to add you in sudoer list.

---

### Post by aysiu on 2008-10-16
Yes, if someone else is managing your computer, ask her to add you as an admin or install the ATI driver for you.

If you somehow accidentally removed yourself from the *sudoers* list, follow these instructions:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by newkomkommer on 2008-10-16
Thanks for your help it worked! :popcorn:

---

