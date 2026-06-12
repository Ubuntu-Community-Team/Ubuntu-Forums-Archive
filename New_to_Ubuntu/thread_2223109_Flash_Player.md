---
title: "Flash Player"
date: 2014-05-09
forum: New to Ubuntu
---

### Post by rickm1945 on 2014-05-09
How do I install Adobe Flash Player 11? Keyring ask for a password, I don't have one.

---

### Post by Thomas_Robert on 2014-05-09
You can install it from, Ubuntu Software Center.
or from terminal 
Enter 
```
sudo apt-get install flashplugin-installer
```
and type your password.

---

### Post by deadflowr on 2014-05-09
> **rickm1945 said:**
> How do I install Adobe Flash Player 11? Keyring ask for a password, I don't have one.

Didn't you set a user password when you installed?
Perhaps a reset is in order
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

then after that's set, look for the flash in the software center, or run this command
```
sudo apt-get install flashplugin-installer
```
this will install flash and also keep it up-to-date.

Edit: ninja'd on the second point.

---

### Post by rickm1945 on 2014-05-09
Yes I do haave a password from install. Keyring didn't accept it. I try again, I could have had a typo.

---

### Post by Amanda_L._Moen on 2014-05-12
Thank you, this was super helpful.

---

