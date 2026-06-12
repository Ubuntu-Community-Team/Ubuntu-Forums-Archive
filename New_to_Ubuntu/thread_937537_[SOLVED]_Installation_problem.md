---
title: "[SOLVED] Installation problem"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by Dacker on 2008-10-04
while i was trying to install AcetoneISO i get across with one of installation's problem. After i entered the password for my account i get this message : Failed to run gdebi-gtk '--non-interactive' '/home/linux/Desktop/acetoneiso_2.0.2-0~getdeb1_i386.deb' as user root.

therefore i su to the root but here is the big problem, it tells me that 
```
Cannot execute /bin/zsh: No such file or directory

```

Thanks in advance ......

---

### Post by adult swim on 2008-10-04
how did you install acetoneISO?

---

### Post by Dacker on 2008-10-04
through the package installer. but the problem now is getting worse so that i couldn't even access my root account and it tells me that 
```
Cannot execute /bin/zsh: No such file or directory

```

yesterday i chsh through the root permissions, therefore i think the problem has occurred there.....

what do you think????

thanks for replying

---

### Post by adult swim on 2008-10-04
so you dont have it installed as of now?
EDIT: it looks like you have tried to install an old version anyway, maybe look here for an install guide [http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html](http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html)
i would suggest Gmount-ISO.  it will let you mount iso images just like isotone and it is available in applications>add/remove

---

### Post by Crafty Kisses on 2008-10-04
Have you used 'tab-completion'? Try that, if that doesn't work try running this command:
```
sudo -i
```
Once you've done that, try it again.

---

### Post by Dacker on 2008-10-04
i've fixed the sudo problem with your clues guys and thank you adult swim for the hilarious link 

thanks again.....

---

### Post by Crafty Kisses on 2008-10-04
No problem, please mark the thread as solved. :D

---

### Post by bulletxt on 2008-10-06
sudo dpkg -i acetoneiso_2.0.2-0~getdeb1_i386.deb

that's all you need to know and do!

---

