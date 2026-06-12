---
title: "configuring auto login timeout"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by degarb on 2012-07-13
I am wondering how to set autologin to 8 seconds.  And set the session to gnome classic no effects, or any other options.   Naturally I would need to know the option:  gnome, gnomeclassic, xfce etc.

Best googling tells me it is in the  sudo gedit /etc/gdm/custom.conf 


Mine reads:
[daemon]
AutomaticLoginEnable=False
AutomaticLogin=dennis
TimedLoginEnable=True
TimedLogin=dennis
TimedLoginDelay=8
DefaultSession=gnome-shell


Am I right?    If this does the time trick.  How do we find out the DefaultSession=    for other environments?  lxde  etc.

---

### Post by Petro Dawg on 2012-07-13
hmm, sorry misread question.  Not sure about proper designation for DefaultSession names.

---

