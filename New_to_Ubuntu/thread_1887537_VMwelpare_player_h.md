---
title: "VMwelpare player h"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by Kickinthedoor on 2011-11-27
ok so im trying to install Vmware-player 4.0.1 on ubuntu 11.10 and im still a noob. i checked the "allow executing file as program' box and when i double click the bundle file it says i need root access. any help or alternative install options would be great.. thanks!

---

### Post by anewguy on 2011-11-27
My personal opinion is to remove what ever you have for VMware, then go to the [Oracle site]("http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html") and download VirtualBox and the extension pack.

I have no idea what it is like now, but I tried VMWare several years ago and found that I just prefer using VirtualBox.

Dave ;)

---

### Post by Majorix on 2011-11-27
You have to run the command
```
gksu nautilus
```
, then locate the file and double click it. If it is designed for Ubuntu it should start the install. If not, you have downloaded the wrong file.

Also make sure you have like at least 4GB memory or everything will start running very slow.

---

### Post by Kickinthedoor on 2011-11-27
> **Majorix said:**
> You have to run the command
```
gksu nautilus
```
, then locate the file and double click it. If it is designed for Ubuntu it should start the install. If not, you have downloaded the wrong file.

Also make sure you have like at least 4GB memory or everything will start running very slow.

I tried the command and I cant find the .bundle file. I know its the linux download, anything else I can try?

---

### Post by Majorix on 2011-11-28
Go to the root folder, then /home, and finally you should see your username there. That's your home folder. The file you downloaded is probably in the Downloads folder. Check around and let me know.

---

