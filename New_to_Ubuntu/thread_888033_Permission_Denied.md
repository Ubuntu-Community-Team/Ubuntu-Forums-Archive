---
title: "Permission Denied"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by silkko on 2008-08-12
silkko@DATA-laptop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
silkko@DATA-laptop:~$ 

everytime i try to access or install a tar.gz or any file through the terminal on the hardy i have this...bash:.............: permission denied..
This is beginning to tick me off since this is my first time using ubuntu..
Can any one offer a helping hand. Thanks a lot... Am using Hardy

---

### Post by nick_h on 2008-08-12
If you are trying to edit a file that is not under your home directory then you will need to either use the *sudo* or *gksudo* command.

For example, to edit /etc/apt/sources.list use:
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by coffeecat on 2008-08-12
It's unclear what you want, but for root access in Ubuntu, read:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

But what are you trying to do with /etc/apt/sources.list? Just typing the path to a file in a terminal in any distro isn't going to get you anywhere. Are you trying to edit it? Try:

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by phidia on 2008-08-12
To protect system critical files only the administrator can access and install to the system.
Use > sudo in front of your commands and be sure you know what you are doing.

---

