---
title: "sudo deborphan | xargs sudo apt-get -y remove --purge ERROR"
date: 2019-01-31
forum: New to Ubuntu
---

### Post by WacoJohn on 2019-01-31
The error is:

```
[COLOR=#242729][FONT=Consolas]administrator@xtrapcpro64:~$ sudo deborphan | xargs sudo apt-get -y remove --purge [/FONT][/COLOR]E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable) 
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?
```

The OS is:

[COLOR=#242729][FONT=Arial]Ubuntu on a thumb drive.[/FONT][/COLOR]
> administrator@xtrapcpro64:~$ cat /etc/*release
DISTRIB_ID=Xtra-PC
DISTRIB_RELEASE=4.1
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Xtra-PC 4.1"
NAME="Ubuntu"
VERSION="16.04.5 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.5 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenialThe objective is to follow this Tutorial:

[https://ubuntuforums.org/showthread.php?t=140920](https://ubuntuforums.org/showthread.php?t=140920)

I am fine until I get to the instruction:

```
sudo deborphan | xargs sudo apt-get -y remove --purge
```

and that is when I get the error.

Any help is appreciated in advance.

---

### Post by again? on 2019-02-02
Close synaptic before running the command.

---

### Post by WacoJohn on 2019-02-02
All I can say is Thank You!!

---

