---
title: "dist-upgrade"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by cyb3rd4wn on 2008-04-27
i use kubuntu feisty 7.04 with gnome installed. i tried upgrading the distro with 
apt-get upgrade   and
apt-get dist-upgrade

it downloaded and installed a bunch of files, however there is no visible change and still it returns:

orion@nether:~$ cat /etc/issue
Ubuntu 7.04 \n \l


is there a way to upgrade distro by terminal or have i misunderstood something?

---

### Post by PmDematagoda on 2008-04-27
Post:-
```
cat /etc/lsb-release
```
Also, in case of a broken upgrade:-
```
dpkg -C
```

---

### Post by Sidewinder1 on 2008-04-27
I was very anxious to upgrade to Hardy Heron 8.04. However it would appear that many folks are having some difficulty with various aspects of the upgrade / update; Since my system (GG 7.10) is working perfectly and I'm new to Ubuntu, I think I'll wait a while... To see some of the questions, check this link:
[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)
HTH

---

### Post by cyb3rd4wn on 2008-04-27
orion@nether:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"
orion@nether:~$ dpkg -C
orion@nether:~$ 


maybe i should retry apt-get dist-upgrade .

---

