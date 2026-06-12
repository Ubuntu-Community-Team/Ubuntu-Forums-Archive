---
title: "Help with MySql v4.1 install"
date: 2006-08-28
forum: Programming Talk
---

### Post by mortsahl on 2006-08-28
I've tried to install MySQL v4.1 several times using Synaptic (on Dapper)... I keep getting the error msg ...

E: /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb: subprocess pre-installation script returned error exit status 1

Can someone tell me what is causing the problem and how I can overcome it?

Thanks

---

### Post by ifokkema on 2006-08-29
You'll need to provide more info. I never use Synaptic, so possibly it hides the most important errors for you.
Try through the console:
```
sudo apt-get install mysql-server-4.1
```
If it fails, send the output and we'll have a look!

---

### Post by mortsahl on 2006-08-29
Thanks for the response.

After an hour or so of Googling I found the answer (in bits and pieces).  Seems that the apt-get remove of MySql v5.0 doesn't fully remove what it needs to, so it leaves files that prevents the installation of MySql v4.1.  Hopefully the Eclipse Web Tools Project will soon support MySql v5 and I can go back to that version.

---

### Post by ifokkema on 2006-08-29
In that case:
```
sudo apt-get remove --purge mysql-server-5.0 && sudo apt-get install mysql-server-4.1
```
will help you out :)

Have fun!

---

