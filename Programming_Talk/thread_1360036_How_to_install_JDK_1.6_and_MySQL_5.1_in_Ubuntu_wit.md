---
title: "How to install JDK 1.6 and MySQL 5.1 in Ubuntu without internet connection."
date: 2009-12-20
forum: Programming Talk
---

### Post by vimodchandra on 2009-12-20
Hi,
 I am a new user of Ubuntu.I am using Ubuntu 8.04 LTS server edition.I want to install **JDK 1.6** and **MySQL 5.1 server** in my system.I dont have an internet connection in the same system.So I cant use apt-get or aptitude commands.But I can download the necessary installation files(or packages ?) using another system(which is having internet connection),and copy the files to my Ubuntu system.
    Please give a detailed explanation and correct links for downloading the necessary installation files.
 I downloaded some packages(.deb files) for MySQL and tried to install using "**dpkg -i**" commands,but I am getting dependency error messages.How can I get all the necessary package files so that I can avoid the dependency issues during installation ? Please help...

---

### Post by sanderd17 on 2009-12-20
If you go use another computer, select the packages you need in synaptic and install it. When synaptic says what packages will be installed, write it down or copie it. 

Install the packages and then copie the installed packages* from /var/cache/apt/archives to a folder you can easy find in the other computer.

Go in synaptic on your other computer to file-> add downloaded packages and select the folder you placed your packages in. 

Than, select the same packages as you selected in synaptic on the first computer and install it. 

This should do it.

*(you can easy find the new packages if you sort them by date)

---

### Post by sanderd17 on 2009-12-20
found something that's even more simple: [aptoncd]("http://aptoncd.sourceforge.net/")
Never tried it, but I think you can use it.

---

