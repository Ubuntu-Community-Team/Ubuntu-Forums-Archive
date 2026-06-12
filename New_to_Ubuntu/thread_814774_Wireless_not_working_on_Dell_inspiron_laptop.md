---
title: "Wireless not working on Dell inspiron laptop"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by dps77 on 2008-06-01
Hello,

I searched the forums for a solution to my problem, but no luck so far.  I just installed Ubuntu onto my Dell inspiron E1405 laptop, and it loads/boots successfully.  However, I cannot get a connection to my wireless network.  I tried connecting via the network manager icon, but after 3-4 attempts (inputting my network name, pass phrase, etc.), it *disappeared* (yes- gone) from the top bar.  At this point, I am totally stuck.  I can't even figure out how to get the manager back.  If anyone can help or point me in the direction of a previously-posted solution, I would greatly appreciate it!

---

### Post by prshah on 2008-06-01
> **dps77 said:**
> However, I cannot get a connection to my wireless network.  I tried connecting via the network manager icon, it *disappeared* (yes- gone) from the top bar.  At this point, 

To get the network manager icon back, press alt+f2, then give the command ```
nm-applet
```. It should reappear instantly. If it doesn't, make sure you have a notification-applet active; right click the panel, choose "Add to Panel..." and choose "Notification Area".

As for the password; gnome/ubuntu stores passwords (such as your wireless password) securely in a "keyring", so that you don't have to reenter passwords everytime. So when the password prompt comes up, check whether it's asking for the keyring password or the wireless password.

---

### Post by Pioneer5000 on 2008-06-01
Try the following link, look for my last post at bottom of page and try those instructions after doing the above stated by prshah.

[http://ubuntuforums.org/showthread.php?t=807979](http://ubuntuforums.org/showthread.php?t=807979)

---

### Post by dps77 on 2008-06-01
> **Pioneer5000 said:**
> Try the following link, look for my last post at bottom of page and try those instructions after doing the above stated by prshah.

[http://ubuntuforums.org/showthread.php?t=807979](http://ubuntuforums.org/showthread.php?t=807979)

**********************

Thanks prshah and Pioneer5000!  Wireless now working!!!

---

