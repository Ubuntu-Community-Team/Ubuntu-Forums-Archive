---
title: "The package ttf-mscorefonts-installer needs to be reinstalled."
date: 2014-02-24
forum: New to Ubuntu
---

### Post by todionut on 2014-02-24
Hello, I`m a beginer  and i have this problem :
> The package ttf-mscorefonts-installer needs to be reinstalled.

I tryed : 
> sudo apt-get install --reinstall ttf-mscorefonts-installer

and the result of this : 
> ionut@iUbuntu:~$ sudo apt-get install --reinstall ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ttf-mscorefonts-installer needs to be reinstalled, but I can't find an archive for it.

OK, now the software center don`t open. :|

P.S. I have Ubuntu 13.10 Saucy Salamander

---

### Post by IvoGuerreiro on 2014-02-24
Hi, 
Try this:
sudo apt-get purge ttf-mscorefonts-installer 
sudo apt-get install ttf-mscorefonts-installer

Form more information, here you have a link: [http://askubuntu.com/questions/367274/i-cannot-install-any-application-anymore](http://askubuntu.com/questions/367274/i-cannot-install-any-application-anymore)
BR

---

### Post by Impavidus on 2014-02-24
Do you have the multiverse repositories enabled? Have a look at your software sources.

---

### Post by todionut on 2014-02-24
> ionut@iUbuntu:~$ sudo apt-get purge ttf-mscorefonts-installer
[sudo] password for ionut: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ttf-mscorefonts-installer needs to be reinstalled, but I can't find an archive for it.


Doesn`t work :( and i tryed averything on that link you gave it to me.

---

### Post by IvoGuerreiro on 2014-02-24
Sorry i could be more helpfull but i'm new on this thing to.
About the software centre give a look on this:
[http://askubuntu.com/questions/342654/the-software-center-wont-start-anymore-how-to-fix-it](http://askubuntu.com/questions/342654/the-software-center-wont-start-anymore-how-to-fix-it)

i found several topics about ttf-mscorefonts-installer errors, but to tell the truth, the procedures they apply are too much complexes me, to indicate as a possible solution.

---

### Post by Vladlenin5000 on 2014-02-24
Post #3 is quite relevant. Please check.

---

### Post by Vladlenin5000 on 2014-02-24
Also you have to loose by trying this:
```
sudo apt-get install -f
```
Make sure you have the multiverse repository as mentioned in post #3 before issuing the command above. You can easily check what repositories you have with a GUI at Software & Updates.

---

### Post by todionut on 2014-02-24
Thank you all to support, I find a way solve the problem with this :

> sudo apt-get -f install
sudo apt-get update 
sudo apt-get dist-upgrade

Thx again for your support.

---

