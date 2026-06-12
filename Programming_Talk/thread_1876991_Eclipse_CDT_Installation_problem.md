---
title: "Eclipse CDT Installation problem"
date: 2011-11-07
forum: Programming Talk
---

### Post by alexandros81 on 2011-11-07
Hi. I have downloaded the Eclipse IDE for C/C++ Linux Developers from Eclipse download page. This is a tar.gz file.
I used the 'tar -xzvf filename.tar.gz' command to unzip it.
It unzips in a folder named 'eclipse'
I change directory to 'eclipse'.
I type the command './configure' but the terminal comes back with the message 'No such file or directory'

Please help! Thanks

---

### Post by georgelappies on 2011-11-07
> **alexandros81 said:**
> Hi. I have downloaded the Eclipse IDE for C/C++ Linux Developers from Eclipse download page. This is a tar.gz file.
I used the 'tar -xzvf filename.tar.gz' command to unzip it.
It unzips in a folder named 'eclipse'
I change directory to 'eclipse'.
I type the command './configure' but the terminal comes back with the message 'No such file or directory'

Please help! Thanks
Why not install it from the repository?

---

### Post by mtangoo on 2011-11-07
sudo apt-get install eclipse-cdt

---

### Post by gusnan on 2011-11-07
I believe the tar.gz that you have downloaded from the eclipse homepage are not a source package, but contains an executable. Search for an executable named "eclipse".

---

