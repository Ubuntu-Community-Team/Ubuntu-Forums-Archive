---
title: "Synaptic packager problem..."
date: 2008-08-29
forum: New to Ubuntu
---

### Post by yogen on 2008-08-29
hello guys...im new to da linux community...its jus a week for me usin ubuntu...
i always get a error whneva in try running Synaptic Package Manager ...
da error says

E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

can neone plz help me wid dis...!!!

---

### Post by Skorzen on 2008-08-29
Try this:
```
sudo dpkg --configure -a
```

---

### Post by tuxxy on 2008-08-29
Run the command as root, add a sudo to the start

---

### Post by yogen on 2008-08-29
it asks fr da admin passwrd...n den...

command not found

---

### Post by tuxxy on 2008-08-29
Your password output may not show up for security reasons, just type it as normal and press enter to run the command

---

### Post by yogen on 2008-08-29
still...nothings done...

yogen@yogen-desktop:~$ sudo dpkg --configure -a
yogen@yogen-desktop:~$ sudo dpkg-- configure -a
sudo: dpkg--: command not found
yogen@yogen-desktop:~$ sudo dpkg  --configure -a
yogen@yogen-desktop:~$

---

### Post by tuxxy on 2008-08-29
> **yogen said:**
> still...nothings done...

yogen@yogen-desktop:~$ sudo dpkg --configure -a
yogen@yogen-desktop:~$ sudo dpkg-- configure -a
sudo: dpkg--: command not found
yogen@yogen-desktop:~$ sudo dpkg  --configure -a
yogen@yogen-desktop:~$

I think you typed it in wrong, just copy and paste this

```
sudo dpkg --configure -a
```

---

### Post by yogen on 2008-08-29
yogen@yogen-desktop:~$ sudo dpkg --configure -a
yogen@yogen-desktop:~$ sudo dpkg --configure -a
yogen@yogen-desktop:~$ sudo dpkg --configure -a
yogen@yogen-desktop:~$ 

still...no use dude..!!!

---

### Post by tuxxy on 2008-08-29
Try removing the package you installed

[https://answers.launchpad.net/ubuntu/+question/20293](https://answers.launchpad.net/ubuntu/+question/20293)

---

### Post by gandaran on 2008-08-29
you need to clear secondlife from synaptic, run this command  
**sudo dpkg --remove --force-remove-reinstreq 'name of the package to remove'**
change name of the package to remove for the exact name of  secondlife package

---

### Post by yogen on 2008-08-29
hey dude...dis is simply awesome...it has workd....
whoaa...

thnk u all million times...
especially 'gandaran'!

---

