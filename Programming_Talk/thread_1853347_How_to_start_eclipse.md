---
title: "How to start eclipse"
date: 2011-10-02
forum: Programming Talk
---

### Post by varunaub on 2011-10-02
I downloaded eclipse and untared the file eclipse-java-indigo-SR1-linux-gtk.tar.gz.The result was an eclipse Directory, It was moved to /usr/local. When I double clicked on the file eclipse the IDE starts But

Name: eclipse
Type : executable

 what is the way to start it through the command line?

---

### Post by logiblocs on 2011-10-02
It is probably easier just to install it through apt -  remove the files you coppied to /usr/local and just run this command:
```
sudo apt-get install eclipse
```

---

### Post by Rocket2DMn on 2011-10-02
Moved to Programming Talk.

Can you not run
```
./eclipse
```
from the install directory?

Eclipse 3.7 "Indigo" will be in the Ubuntu 11.10 repositories coming out in a couple of weeks.

---

### Post by varunaub on 2011-10-03
> It is probably easier just to install it through apt -  remove the files you coppied to /usr/local and just run this command:
 	Code:
 	sudo apt-get install eclipse 

Yes It's easy But the problem is When eclipse is installed using apt-get the default JDK and JRE(default- java and java-1.5.0-gcj-4.5)for Linux gets installed, I want to prevent that since I have already installed openjdk

---

### Post by taurial on 2011-10-03
You can choose desired version after running in terminal:

sudo update-alternatives --config java

It is also possible to remove unnecessary java versions later on.

---

