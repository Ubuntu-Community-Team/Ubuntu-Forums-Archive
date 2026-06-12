---
title: "HowTo: Install the newest Amarok in Gnome"
date: 2006-07-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Athanasius on 2006-07-22
I don't know about other people but I can't stand Rhythm Box and the version of Amarok in the repositories is old so here is the new one from the Kubuntu website.

open your ect/apt/sources.list
> sudo gedit /ect/apt/sources.list

add this line at the end and save:
> deb [http://kubuntu.org/packages/amarok-141](http://kubuntu.org/packages/amarok-141) dapper main

then open terminal and type:
>  wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
 sudo apt-key add kubuntu-packages-jriddell-key.gpg

then type:
> sudo apt-get update

then type:
> sudo apt-get install amarok

That should be it.  If anyone has any corrections please let me know

---

### Post by vuitton on 2006-07-23
Hi, thanks for the HowTo.

There's a typo here, though : )

sudo gedit /**ect**/apt/sources.list

Furthermore, there seems to be another problem.
vuitton@vuitton-desktop:~$ wget [http://people.ubuntu.com/~jriddell/k...iddell-key.gpg](http://people.ubuntu.com/~jriddell/k...iddell-key.gpg)
--12:19:44--  [http://people.ubuntu.com/~jriddell/k...iddell-key.gpg](http://people.ubuntu.com/~jriddell/k...iddell-key.gpg)
           => `k...iddell-key.gpg'
Auflösen des Hostnamen »people.ubuntu.com«.... 82.211.81.132
Verbindungsaufbau zu people.ubuntu.com|82.211.81.132|:80... verbunden.
HTTP Anforderung gesendet, warte auf Antwort... 404 Not Found
12:19:46 FEHLER 404: Not Found.
EDIT: Problem solved, shouldn't c&p that much : ) thank you mamato

---

### Post by mamato on 2006-07-23
if you have a problem, you can consult this page : 
[http://kubuntu.org/announcements/amarok-1.4.1.php](http://kubuntu.org/announcements/amarok-1.4.1.php)

> **vuitton said:**
> Hi, thanks for the HowTo.


There's a typo here, though : )

sudo gedit /**ect**/apt/sources.list

Furthermore, there seems to be another problem.
vuitton@vuitton-desktop:~$ wget [http://people.ubuntu.com/~jriddell/k...iddell-key.gpg]("http://people.ubuntu.com/%7Ejriddell/k...iddell-key.gpg")
--12:19:44--  [http://people.ubuntu.com/~jriddell/k...iddell-key.gpg]("http://people.ubuntu.com/%7Ejriddell/k...iddell-key.gpg")
           => `k...iddell-key.gpg'
Auflösen des Hostnamen »people.ubuntu.com«.... 82.211.81.132
Verbindungsaufbau zu people.ubuntu.com|82.211.81.132|:80... verbunden.
HTTP Anforderung gesendet, warte auf Antwort... 404 Not Found
12:19:46 FEHLER 404: Not Found.

---

### Post by lizzard on 2006-07-23
```
wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
```

---

### Post by Taiden on 2006-07-23
this is great and everything.. but what about MP3 support? :D

---

### Post by ryan on 2006-07-23
Tks this is great really works well..

---

### Post by hopstah on 2006-07-23
any word on m4b support?

---

### Post by atrus123 on 2006-07-24
Thanks for the info.  Installing it now.

---

### Post by joshier on 2007-03-22
It's actually ... 
> 1. in terminal, sudo gedit /etc/apt/sources.list
2. add "deb http://kubuntu.org/packages/amarok-145 edgy main" (then save)
3. in terminal,  wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
sudo apt-key add kubuntu-packages-jriddell-key.gpg
4. apt-get update
5. apt-get install amarok amarok-engines
(5 optional) sudo apt-get install amarok


---

