---
title: "Netbeans Installation failure"
date: 2016-03-11
forum: New to Ubuntu
---

### Post by clement-harambe on 2016-03-11
$ sudo app-get install jdk-7u71-linux-i586.rpm  netbeans-8.0.1-linux.sh
sudo: app-get: command not found

Is there a better way to download and install netbeans compilers?:(

---

### Post by QIII on 2016-03-11
Hello!

First, you should be using the .deb not the .rpm.  Ubuntu is in the Debian family and uses .deb.  Go back to the download site and get the .deb package.

Second, the command is apt-get not app-get.

Cheers!

---

### Post by slickymaster on 2016-03-11
Hi clement-harambe, welcome to the forums.

First,  **jdk-7u71-linux-i586.rpm** is the wrong package, since it isn't for Ubuntu/Debian based systems.

So, if you want to install Netbeans in Ubuntu, first download the correct bundle (Netbeans + Oracle JDK) for your system architecture from [https://netbeans.org/downloads/](https://netbeans.org/downloads/)

Once that done, navigate to the folder where the donload bundle is and give the correct permissions to the executable, by running the following command in a terminal window```
chmod +x ~/path_to_folder/netbeans-8.1-javase-linux.sh
```Once that done execute the installer```
cd ~/path_to_folder/ && ./netbeans-8.1-javase-linux.sh
```

---

