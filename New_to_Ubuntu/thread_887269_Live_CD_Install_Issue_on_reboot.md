---
title: "Live CD Install Issue on reboot"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by prunk on 2008-08-12
I've run the Ubuntu live CD on an atom board and it runs just fine. Well not perfectly but that was a monitor issue. 
However, I finally got my 4GB CF card so I decided to install Ubunutu to the CF card. The CF card is connected to the motherboard with an IDE adapter and is recognized in the BIOS as a Hard Drive connection.
So the install went through fine. Then I restarted and put in my new user name and password and it was accepted there. No apparent boot problems so far. However directly after the login was completed the screen remains at an intermediate loading screen where all I can see is the mouse and an off white background. I've scrolled the mouse up and down, it's not a resolution problem. Any suggestions?

---

### Post by tech0007 on 2008-08-12
Press 'ctrl-alt-F1' and login to a console. Type 'sudo /etc/init.d/gdm restart'.  If you get that blank white screen again, check /var/log/Xorg.0.log for errors. You can post it here.

---

### Post by prunk on 2008-08-12
gdm restart worked fine. took me to the login screen looked all nice and what not but when i log in again it just goes to the same offwhite background and mouse but nothing else

then i tried 
/var/log/Xorg.0.log
i tried this in both user and root and in both cases i was just given a permission deinied line.

---

