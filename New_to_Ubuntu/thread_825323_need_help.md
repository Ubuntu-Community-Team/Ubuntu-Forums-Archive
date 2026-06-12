---
title: "need help"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by glb48 on 2008-06-10
you must manually run 'dpkg --configure -a' to correct the problem. 
 how do i fix this new to ubuntu

---

### Post by Gannon8 on 2008-06-10
Open a terminal (Applications > Accessories > Terminal) then copy and paste that command. Wait for it to finish.

---

### Post by Ripfox on 2008-06-10
Go to applications/accessories/terminal and type in it

> sudo dpkg --configure -a

you have to run it as root I think

---

### Post by Joeb454 on 2008-06-10
Open a terminal - Applications > Accessories > Terminal

And then copy/paste this command into it ```
sudo dpkg --configure -a
``` It will ask for your password - enter that (it will **not show any characters being entered** - but rest assured that it is reading your password).

After that it should be ok :)

Also please try to use a more descriptive thread title in future, it helps people know what the thread is about :)

Edit: this error confuses a lot of people - but it **needs** to be run as root

---

### Post by bluepowder7 on 2008-06-10
applications - accessories - terminal
then type that in the terminal window

---

### Post by Ripfox on 2008-06-10
> **Joeb454 said:**
> this error confuses a lot of people - but it **needs** to be run as root

yes...as I posted...

---

