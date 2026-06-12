---
title: "Nvidia drivers installation GCC kernal?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by gamer4lyf3 on 2008-05-16
Hey everyone! I'm trying to install the drivers for my Nvidia card using this post [http://ubuntuforums.org/showthread.php?p=4908847&posted=1#post49088477](http://ubuntuforums.org/showthread.php?p=4908847&posted=1#post49088477)  but every time I go to install I get an error about now having the correct Kernel it says that my current Kernel gcc 4.1(or 4.2 cant remember) doesn't match with 4.2(or 4.1 cant remember order). I'm kind of at a loss at how to make them the same? some help please? :)

---

### Post by dizee on 2008-05-16
You may need to install the GNU c compiler (gcc). You can install both to be sure:```
sudo apt-get install gcc-4.1 gcc-4.2
```

---

### Post by gamer4lyf3 on 2008-05-17
Thanks for the reply! but when I ran that It told me...
gcc-4.1 is already the newest version.
gcc-4.2 is already the newest version.
gcc-4.2 set to manually installed.
and then it gave me some packets it called useless that I could remove.

---

### Post by jespdj on 2008-05-17
Install the packages build-essential and linux-headers-generic:
```
sudo apt-get install build-essential linux-headers-generic
```
Those packages contain files that the compiler needs to be able to compile kernel modules.

---

### Post by Xiong Chiamiov on 2008-05-17
The issue is that the command "gcc" points toward 4.2, while the kernel was compiled with 4.1.  You can change where it links by doing this:
```

cd /usr/bin
sudo rm gcc
sudo ln -s gcc-4.1 gcc

```

---

