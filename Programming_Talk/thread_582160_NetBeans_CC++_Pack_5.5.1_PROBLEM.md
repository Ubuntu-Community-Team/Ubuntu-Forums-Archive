---
title: "NetBeans C/C++ Pack 5.5.1 PROBLEM"
date: 2007-10-19
forum: Programming Talk
---

### Post by psychok7 on 2007-10-19
hi there. i have netbeans and jdk installed by the repository, but when i try to install d C/c++ pack it says i have to enter the correct location of the IDE intaller files,(usr/share/netbeans)... so i do that and it says the location is incorrect... i cant seem to find another location.. any ideas??

---

### Post by craighamilton on 2007-10-22
I just did this today. You need to install as the super user so use sudo ./netbeans-c++-5_5_1_u1-linux.bin and then do the install wizard steps as normal.

Happy coding!

---

### Post by psychok7 on 2007-10-22
thats wht i do, but it still says that thats not the right folder

---

### Post by craighamilton on 2007-10-22
Try the /usr/share/netbeans/5.5 folder as your netbeans install folder for the wizard.

---

### Post by rekahsoft on 2007-10-22
i always install to /opt/Sun...and i just chown the directory when i am installing using the binary installer from [http://netbeans.org](http://netbeans.org)
but i do not know where the deb installs..AFAIR it is somewhere in /usr...try:```
locate netbeans
```

---

### Post by psychok7 on 2007-10-25
i installed trough apt-get... i know were the files are.. but when i try to install it it still says its not there.. and i use sudo

---

### Post by psychok7 on 2007-11-27
my problem is solved the solution is in netbeans folder in /usr/share/netbeans/5,5

---

