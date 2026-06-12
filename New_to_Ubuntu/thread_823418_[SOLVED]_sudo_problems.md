---
title: "[SOLVED] sudo problems"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by wabbit46 on 2008-06-09
After several problems I re-installed Ubuntu. Now sudo wont work.
It gives the reply unable to resolve <computer name>

Can anyone advise me what I have done wrong ?

---

### Post by bluefrog on 2008-06-09
check /etc/hosts and hostname

/etc/hosts
127.0.0.1 localhost machine

/hostname
machine

---

### Post by wabbit46 on 2008-06-09
The hosts file entry is incorrect. But the hostname entry is correct. Can the hosts file be edited ?

---

### Post by bluefrog on 2008-06-09
you need to boot in recovery mode and edit the file

nano /etc/hosts

---

### Post by ibutho on 2008-06-09
Yes it can be edited e.g. "sudo nano /etc/hosts".

---

### Post by ukripper on 2008-06-09
> **wabbit46 said:**
> The hosts file entry is incorrect. But the hostname entry is correct. Can the hosts file be edited ?

yes to edit use the following command in terminal :
```
sudo gedit /etc/hosts
```

if sudo doesnt work then try :
```
su -i
```

to be in root mode

---

### Post by miss.magenta on 2008-06-09
run sudo ./etc/init.d/hostname.sh hostname to change your hostname - this should be run even if you've edited /etc/hosts manually and even if you have run sudo hostname to change it.

oh, and you should also edit the /etc/hostname file (different from /etc/hosts) and then do sudo /etc/init.d/networking restart

---

