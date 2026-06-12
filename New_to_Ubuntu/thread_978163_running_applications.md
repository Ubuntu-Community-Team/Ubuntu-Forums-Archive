---
title: "running applications"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by irish66 on 2008-11-10
how do i get an application to run if not in applications, or typing name in terminal doesn't do the job.
m

---

### Post by tuxxy on 2008-11-10
It will run from terminal but you probably have got an incorrect command, whats the program you are trying to find?

---

### Post by MrWES on 2008-11-10
> **irish66 said:**
> how do i get an application to run if not in applications, or typing name in terminal doesn't do the job.
m

[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

Nice resource; click on the install software link on the left side.

Bill

---

### Post by irish66 on 2008-11-10
there is one called ampache in synthatic, 
here's what i did in terminal and response i got. it has a green box beside it in syn
irish@ubuntu:~$ ampache
bash: ampache: command not found
irish@ubuntu:~$ 
Thanks for link.
M

---

### Post by zvacet on 2008-11-10
In main menu under internet or audio &sound on the left side choose where you want to put that app.On the right side select new item and then new launcher will pop up.What is imprtant here is right path to the executable file.In most cases they are under /usr/bin .You can find where app is by typing in terminal

```
locate ampache
```

or in synaptic right click on that app and under properties (I think) you will see where is installed.

When you give right path for your app name it and add icon (look in /usr/share/pixmaps).This should make launcher for your app and you will see it under applications.

---

### Post by irish66 on 2008-11-10
still no luck, thanks anyhow.
M

---

### Post by irish66 on 2008-11-11
Sorry, it was getting really late last night(this morning), which is why I didn't give a detailed answer.
1.locate ampache
irish@ubuntu:~$ locate ampache
irish@ubuntu:~$

2. ampache folder is located in usr/share
ie there is a folder called usr/share/ampache
But I guess I still need to know, the file that actually launches the program.
M

---

### Post by cjssmo on 2008-11-26
Just found this post, ampache is not a c+ app it is a web app.  So if you installed ampache from the repositories insure apache2 and mysql-server are running, then open your web browser and point it to your ampache install for example 

[http://localhost/ampache](http://localhost/ampache)

or

[http://your.ip.address/ampache](http://your.ip.address/ampache)

This will bring you to the web install interface.

Have a look at 

[http://ubuntuforums.org/showthread.php?t=546007&highlight=ampache+easy](http://ubuntuforums.org/showthread.php?t=546007&highlight=ampache+easy)

---

### Post by irish66 on 2008-11-26
Thank you. I've kind of totally forgotten all about this thing.

---

