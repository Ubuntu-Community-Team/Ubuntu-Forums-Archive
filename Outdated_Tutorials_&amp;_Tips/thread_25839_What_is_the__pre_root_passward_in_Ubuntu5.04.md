---
title: "What is the  pre root passward in Ubuntu5.04?"
date: 2005-04-11
forum: Outdated Tutorials &amp; Tips
---

### Post by zmcid9 on 2005-04-11
I have finished installing the Ubuntu5.04,I wanted to shift to the root,but I don't have the root passward.What is the default root password?Is it pre set in the system?Thank you!

---

### Post by heimo on 2005-04-11
You can run programs as a root with sudo, or if you want to use root account "as usual", you can set its password with
```
sudo passwd root
```
enter this in terminal or console (command prompt), type new root passwd twice and you're ready to root. :) Remember not to use root account for anything other than neccessary administration tasks (editing system wide config files, installing software). Don't log into X using root, don't use it as your regular user account.

---

### Post by sassur on 2005-04-11
There is no root password in Ubuntu, the root account is disabled. If you want to do admin stuff you should use sudo.

example:
$ sudo nano /etc/apt/sources.list

when it askes for password enter your user password.

more info about sudo [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

---

