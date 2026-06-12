---
title: "How do I install software as root?"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by RichTJ99 on 2008-11-12
Hi,

I recompiled virtualbox for Lpia in Ubuntu 8.04.  The Vbox team seems to think that my problem is the file permissions are wrong.  The file on my desktop is called virtualbox-2.0.deb

[email]root@rich:/home/rich/Desktop/virtualbox-2.0.deb[/email] 

How can I force the install as root in terminal?

Or how can I log in as root?

Thanks,
Rich

---

### Post by taurus on 2008-11-12
You don't have to log in as root to install something with root privilege.  You just need to put sudo in front of the command.

```
cd ~/Desktop
sudo dpkg -i virtualbox-2.0.deb
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tvtech on 2008-11-12
sudo -i 


this will give you a root user session until you exit.  that way you don't have to assign a root password.  stick with sudo don't assign root a password, it's safer.

---

### Post by tvtech on 2008-11-12
you can also change your permissions using chmod

check out info chmod for how to use it. 

```
 I LOVE ROOT:~$ sudo chmod +uarwx virtualbox-2.0.deb

```

---

