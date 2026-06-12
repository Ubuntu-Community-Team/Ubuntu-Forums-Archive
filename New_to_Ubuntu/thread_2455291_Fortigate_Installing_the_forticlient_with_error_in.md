---
title: "Fortigate: Installing the forticlient with error in the repository"
date: 2020-12-16
forum: New to Ubuntu
---

### Post by victorinorj on 2020-12-16
Good night experts.
I'm trying to install the client fortine on Ubuntu 16.04LTS.
I'm following the procedure below:
> wget -O - https://repo.fortinet.com/repo/ubuntu/DEB-GPG-KEY">[https://repo.fortinet.com/repo/ubuntu/DEB-GPG-KEY](https://repo.fortinet.com/repo/ubuntu/DEB-GPG-KEY) | sudo apt-key add -
> deb [arch = amd64] [https://repo.fortinet.com/repo/ubuntu/](https://repo.fortinet.com/repo/ubuntu/) xenial multiverse
> sudo apt-get update
> sudo apt install forticlient


However I have the following error when I try to update the repository.
fox @ fox: ~ $ sudo deb [arch = amd64] [https://repo.fortinet.com/repo/ubuntu/](https://repo.fortinet.com/repo/ubuntu/) xenial multiverse
sudo: fox machine could not be resolved
sudo: deb: command not found
fox @ fox: ~ $
fox @ fox: ~ $ sudo apt install forticlient


sudo: fox machine could not be resolved
Reading package lists ... Done
Building dependency tree
Reading status information ... Ready
E: The omada package needs to be reinstalled, but it was not possible to find a file for it.
fox @ fox: ~ $


Can someone who needed to install help me?

---

### Post by wildmanne39 on 2020-12-16
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by grahammechanical on 2020-12-16
Please run this command

```
cat /etc/apt/sources.list
```

Look through the printout to confirm that 

> deb [arch = amd64] [https://repo.fortinet.com/repo/ubuntu/](https://repo.fortinet.com/repo/ubuntu/) xenial multiverse

is listed as a repository source. To update/upgrade installed packages we run

```
sudo apt-get update
sudo apt-get upgrade
```

Or to use the more recent version of those commands

```
sudo apt update
sudo apt upgrade
```

If the fortinet repository is listed as a repository and the forticlient package is installed, then those two commands will update/upgrade the forticlient package if it needs upgrading.

You used the wrong command to update the repository. Typing the repository address in a terminal does not update the repository. That is why you saw "deb: command not found" 

You instructed the terminal to run a command called "deb" which does not exist in Linux.

Regards

---

