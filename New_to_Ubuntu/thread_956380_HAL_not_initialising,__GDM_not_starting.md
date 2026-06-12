---
title: "HAL not initialising,  GDM not starting"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by dave.com on 2008-10-23
I use graphical login and get bitchslapped by pop up error "user /home/<user>/.dmrc is being ignored". Session lasts less than 10secs. 
Login Session change to FailSafe X-Terminal session, and see the /home partition is not mounted. So I mount it, so far so good. 

Issuing StartX, I get launched into a priviledged root session. Once there I don't have GParted anymore. I don't have permission to open Applications like Services, Users&Groups, Authorisations either. 

I check /etc/fstab its A-OK. Run ntfs-config, HAL popup reports an error then the 'normal' popup window also pops up. Check grub detection of disk partitions and menu.lst they're fine. X-Server and nvidia-settings work but do not find a screen for user except as root. 

Something about Xauthority too.. talking about /home somewhere.

Changing login to another user fails. Gnome Desk applet fastswitcher or something, root asks if I wish to delete it coz its being a bad boy. Comp just crashes to command console.

Finally, also no internet from root Desktop.

Somebody know what's going on? How do I fix all that?

---

### Post by dave.com on 2008-10-23
moving topic to Desktop & Environment

---

