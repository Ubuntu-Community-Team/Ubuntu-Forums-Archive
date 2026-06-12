---
title: "how do i remove wine (really remove it)"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by e1ektrob0y on 2008-05-18
how do i completely remove all traces of wine from my system? I am trying to uninstall photoshop but the wine uninstaller doesn't work it just keeps saying "the installer was interrupted you system has not been changed". When i try to run wine uninstaller with sudo it says "you are not the owner of /.wine"

I tried 
```
sudo apt-get remove wine
```

and then i deleted the /.wine directory but after a reboot wine still appears in the applications drop down menu?? 

Its really annoying me :(

---

### Post by Victormd on 2008-05-18
Remove this as well
> ~/.local/share/applications/wine
then remove any dependencies that are not used with (don't add anything to it, this command will automatically remove any dependency that's not being used)
```
sudo apt-get autoremove
```
Now, for the menu, go to SYSTEM>PREFERENCES>MAIN MENU and remove them there...

---

### Post by e1ektrob0y on 2008-05-18
that worked thanks :D

---

