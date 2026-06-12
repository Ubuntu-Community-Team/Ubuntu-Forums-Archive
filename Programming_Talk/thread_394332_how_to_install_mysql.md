---
title: "how to install mysql"
date: 2007-03-26
forum: Programming Talk
---

### Post by b3rx on 2007-03-26
I dont have an internet connection in my ubuntu box so i was wondering what packages do i need so that i could use mysql. im trying to setup a LAMP system.

please advice.

should installing mysql-client-5.0 in the repos and its deps enough? or i need it install some other packages?

---

### Post by will_in_wi on 2007-03-26
Not extremely easy, but the way to do this is to open a terminal and type:
```
sudo apt-get install -ds mysql-server
```
The output will tell you all of the packages that will be installed. Then go to packages.ubuntu.com and download the .deb files for all of the packages on the list. Get the downloaded packages on the computer you are trying to install mysql on in a single folder. Open a terminal and navigate to the folder. To install type:
```
dpkg -i *.deb
```
You should now have mysql installed.

---

### Post by Mirrorball on 2007-03-26
> **b3rx said:**
> I dont have an internet connection in my ubuntu box so i was wondering what packages do i need so that i could use mysql. im trying to setup a LAMP system.

please advice.

should installing mysql-client-5.0 in the repos and its deps enough? or i need it install some other packages?
You need **mysql-server** too.

---

### Post by b3rx on 2007-03-26
> **will_in_wi said:**
> Not extremely easy, but the way to do this is to open a terminal and type:
```
sudo apt-get install -ds kubuntu-desktop
```
The output will tell you all of the packages that will be installed. Then go to packages.ubuntu.com and download the .deb files for all of the packages on the list. Get the downloaded packages on the computer you are trying to install mysql on in a single folder. Open a terminal and navigate to the folder. To install type:
```
dpkg -i *.deb
```
You should now have mysql installed.

why the need for kubuntu-desktop?

---

### Post by b3rx on 2007-03-26
> **Mirrorball said:**
> You need **mysql-server** too.

so its mysql-client and mysql-server and their respective deps then im good to go right?

---

### Post by will_in_wi on 2007-03-26
oops sorry about that. I have mysql installed so I used kubuntu-desktop as a test on my machine and forgot to change it when I posted it. I will edit it. You can replace kubuntu-desktop with anything and the command will show you the deps of a package.

---

### Post by Mirrorball on 2007-03-26
> **b3rx said:**
> so its mysql-client and mysql-server and their respective deps then im good to go right?
Yes.

---

