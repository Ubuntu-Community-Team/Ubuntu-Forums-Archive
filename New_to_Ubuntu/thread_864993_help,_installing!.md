---
title: "help, installing!"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by alanvxx on 2008-07-20
hey i need a little help, i'm new to ubuntu and everytime i try to install something i keep getting this error.

[IMG]http://i46.photobucket.com/albums/f110/alanvxx/Screenshot1.png[/IMG]

any help would be appreciated.

---

### Post by deanjm1963 on 2008-07-20
Quite easy to fix.

Open up a terminal and type the following:

sudo dpkg --configure -a

hit enter, type your password and it should fix the problem.

---

### Post by billgoldberg on 2008-07-20
> **deanjm1963 said:**
> Quite easy to fix.

Open up a terminal and type the following:

sudo dpkg --configure -a

hit enter, type your password and it should fix the problem.

That will do it.

From the screenshot I see you are using amarok on gnome.

[Exaile]("apt://exaile") would be better.

---

### Post by alanvxx on 2008-07-20
ha thanks guys, that worked like charm, so i should uninstall amarok and use exaile?

---

### Post by alanvxx on 2008-07-20
now i'm getting an error message, another synaptic is running, and also broken files, please fix these before you update! argh!

---

### Post by Xerp on 2008-07-20
> **alanvxx said:**
> now i'm getting an error message, another synaptic is running, and also broken files, please fix these before you update! argh!

Close Update Manager and re-run the terminal command :)

---

### Post by MattBD on 2008-07-20
> **alanvxx said:**
> now i'm getting an error message, another synaptic is running, and also broken files, please fix these before you update! argh!

Can you post a screenshot of this?

---

### Post by alanvxx on 2008-07-20
i'm getting this "alan@alan-laptop:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
alan@alan-laptop:~$"

and this..

[IMG]http://i46.photobucket.com/albums/f110/alanvxx/Screenshot2.png[/IMG]

---

### Post by MattBD on 2008-07-20
OK, basically only one instance of apt-get can run at once. Synaptic is just a graphical front end for apt-get.
To resolve the issue about broken packages, enter this:
```
sudo apt-get -f install
```
Apt will automatically resolve any unmet dependencies.

---

### Post by alanvxx on 2008-07-20
and then i get this..

alan@alan-laptop:~$ sudo apt-get -f install
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
alan@alan-laptop:~$ 

?

---

### Post by MattBD on 2008-07-20
It looks like there's another instance of apt running already, so you can't use it. I'd reboot, that way you know there isn't an instance running. Then run sudo apt-get -f install again.

---

