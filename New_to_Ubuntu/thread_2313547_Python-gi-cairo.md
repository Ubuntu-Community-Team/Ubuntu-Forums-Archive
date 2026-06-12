---
title: "Python-gi-cairo"
date: 2016-02-13
forum: New to Ubuntu
---

### Post by dan_williscroft on 2016-02-13
What does this error mean?

python-gi-cairo : Depends: python-gi (= 3.12.0-1) but 3.12.0-1ubuntu1 is to be installed

Also

he following packages have unmet dependencies.
 openssh-server : Depends: openssh-client (= 1:6.6p1-2ubuntu2.4) but 1:6.6p1-2ubuntu2.6 is to be installed
                  Recommends: ncurses-term but it is not going to be installed
                  Recommends: ssh-import-id but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

My packages are clearly broken but I dunno how to repair them.

---

### Post by grahammechanical on 2016-02-13
It depends on what you were doing or what you were trying to install. And where you downloaded the package from. Generally, this is the command to fix broken packages. It is often suggested to use this command by apt-get in this situation. Have you tried it?

```
sudo apt-get install -f
```

Regards.

---

### Post by dan_williscroft on 2016-02-13
trying to install openssh and ubuntu software centre. I am using lubuntu 14.04 ppc edition

---

