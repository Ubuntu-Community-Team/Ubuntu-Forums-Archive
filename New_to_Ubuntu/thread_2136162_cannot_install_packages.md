---
title: "cannot install packages"
date: 2013-04-16
forum: New to Ubuntu
---

### Post by JohntheChristian on 2013-04-16
every time i try to install a .deb in the last couple days, I am getting the messages about "broken dependencies" or "broken Cache". I tried to read similar issues on the forums and try some of the commands advised there, but to no resolution. 

I even tried to write over lubuntu with a fresh install, but when i put in my live cd it just loaded my desktop.

---

### Post by ibjsb4 on 2013-04-16
Problem #1  Open a terminal and enter:

```
sudo apt-get update
```

Get any errors?

---

### Post by JohntheChristian on 2013-04-16
> **ibjsb4 said:**
> Problem #1  Open a terminal and enter:

```
sudo apt-get update
```

Get any errors?

Doesn't seem like it. a lot happened when i ran it, last line says Reading package list....... Done

---

### Post by ibjsb4 on 2013-04-16
Ok, your half way there

```
sudo apt-get upgrade
```

What happens?

---

### Post by JohntheChristian on 2013-04-16
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gens:i386 : Depends: xdg-utils:i386 but it is not installable
E: Unmet dependencies. Try using -f.




When i do run apt-get -f install I get

> tommy@tommy-Presario-CQ62-Notebook-PC:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


---

### Post by ibjsb4 on 2013-04-16
Did you put a sudo in front of that apt-get -f install?

sudo apt-get -f install

---

### Post by JohntheChristian on 2013-04-16
no, will do now. Got this:
 

Removing gens ...Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...

thanks for your help btw, should i try another installation now, or is there more?

---

### Post by ibjsb4 on 2013-04-16
Try another upgrade

and your welcome :)

---

