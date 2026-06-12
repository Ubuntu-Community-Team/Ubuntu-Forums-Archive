---
title: "Java for Mozilla (and other things)"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by kenizl86 on 2012-11-04
Hey,

   Is there anyway to get java to work on Xubuntu 12.04? I need it to go on [www.virtualnes.com](www.virtualnes.com), which uses java plugins.

   I would also like to know how to get it so  I can play things like "Legends of Yore" on my comp, which uses the not-online-version.

        Thanks!

---

### Post by Abhinav Kumar on 2012-11-04
> **kenizl86 said:**
> Hey,

   Is there anyway to get java to work on Xubuntu 12.04? I need it to go on [www.virtualnes.com]("http://www.virtualnes.com"), which uses java plugins.

   I would also like to know how to get it so  I can play things like "Legends of Yore" on my comp, which uses the not-online-version.

        Thanks!
Hi

I don't know whether it will work for Xubuntu but the following steps had worked for ubuntu .

Download latest jre package.
Extract it to the home folder
Say the folder is jre-1.7.0.0

You need libnpjp2.so to run java.

So better make a symbolic link of the same name and point it to the the downloaded folder

Type in terminal
```
sudo -i
cd /usr/lib/mozilla/plugins
ln -s ~/jre-1.7.0.0/lib/amd64/libnpjp2.so
```

Regards,
Abhinav

---

### Post by Cheesemill on 2012-11-04
Or you could use the easy method:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

This method ensures that Java is automatically kept up to date along with the rest of your system.

---

### Post by kenizl86 on 2012-11-04
> **Cheesemill said:**
> Or you could use the easy method:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```This method ensures that Java is automatically kept up to date along with the rest of your system.

I did that, and I went to Xfce>System>Oracle Java 7 Console, and clicked it. It Brought up an error that said: "Failed to execute child process "/usr/lib/jvm/java-7-oracle/jconsole" (No such file or directory)".

I also tried to play a game on virtualnes, but to no avail. How can I get it to work in Mozilla?

---

### Post by kenizl86 on 2012-11-04
Anyone?

---

### Post by Abhinav Kumar on 2012-11-05
> **kenizl86 said:**
> Anyone?
If possible try the 1st reply. see if something works

---

### Post by kenizl86 on 2012-11-12
It's working now on virtualnes.com, but it plays the games slow. Like, VERY slow. Any way to fix this? Is it Java?

---

