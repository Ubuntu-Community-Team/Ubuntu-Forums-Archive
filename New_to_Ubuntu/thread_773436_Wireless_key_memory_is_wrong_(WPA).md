---
title: "Wireless key memory is wrong (WPA)"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Iago1989 on 2008-04-28
I have a wireless key and it is about ************ long, and when I restart my computer, Ubuntu has it about ************************* long, and I can't get on the internet. So every time I restart I have to rewrite the key, which is not fun :-P

---

### Post by Helios1276 on 2008-04-28
would ticking 'show password' shed some light?

---

### Post by Iago1989 on 2008-04-28
There is no box to tick?

---

### Post by anewguy on 2008-04-29
Assuming you are using Ubuntu, go to System, then Administration, then over to and click on Keyring Manager.  You can modify, delete, click "show password" there.  Hopefully you should be able to work out your problem, as this is where the password in question is stored.  :)

---

### Post by Iago1989 on 2008-04-29
There is no such thing in the administrator menu. The only thing called keyring is in the preferences, which I added a "wireless" keyring it but it didn't really help. I'm using ubuntu 8.04

---

### Post by anewguy on 2008-04-29
> **Iago1989 said:**
> There is no such thing in the administrator menu. The only thing called keyring is in the preferences, which I added a "wireless" keyring it but it didn't really help. I'm using ubuntu 8.04

With normal Ubuntu, across the top line of your screen will be the Ubuntu symbol, Applications, Places and System.  Click System -> if Administration doesn't show there you have bigger problems.  As a last resort, you could always delete the keyring file:  mine is under my user name as follows:

/home/dave/.gnome2/keyrings/login.keyring


It used to be that deleting that file would cause the pam keyring manager to prompt you next time for the keyring password and recreate the keyring entry for your network.

---

### Post by Iago1989 on 2008-04-29
Administration is there, but keyring mananger is not.

---

### Post by Iago1989 on 2008-04-29
perhaps this might help...it's WPA personal....and ASCII

---

### Post by Alldan on 2008-04-29
try wicd 
more information here: [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
you must put your right password in system - administration - network then in wicd advanced settings. !!Wicd wil remove an replace network-manager

---

### Post by Iago1989 on 2008-04-29
Seems to work. It was sort of tricky though...I had to have the administrator password application open while I connected in wicd...but it worked.

---

