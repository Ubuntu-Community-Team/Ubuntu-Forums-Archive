---
title: "copy from home/Downloads to usr/java"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by mohsen12 on 2013-07-16
Hello everybody
I am trying to copy    [ re-7u25-Linux-x64. tar. gz] from home/Downlods     to usr/java  using cp
By following command

```

root@mohsen-Aspire-5740:/home/mohsen/Downloads# sudo cp jre-7u25-linux-x64.tar.gz  /usr/java

//It gives this error
cp: cannot stat `jre-7u25-linux-x64.tar.gz': No such file or directory



```
Thank you
 Second day using of Linux

---

### Post by QIII on 2013-07-16
Hello!

May I first ask what you are trying to accomplish?

Thanks!

---

### Post by dannyboy79 on 2013-07-16
if you're trying to install java jre there is a ppa you can install to get java 7 installed. i don't know exactly what you're trying to accomplish so if you could answer QIII question that would help us help you.

copying that file to that directory would be
```
sudo cp jre-7u25-linux-x64.tar.gz  /usr/java/
```
you were just missing the end slash, but that will only work IF there is a directory located at /usr/java/

---

### Post by mohsen12 on 2013-07-16
> **QIII said:**
> Hello!

May I first ask what you are trying to accomplish?

Thanks!
I try to execute the order of this WEBPAGE (install)
[http://java.com/en/download/help/linux_x64_install.xml](http://java.com/en/download/help/linux_x64_install.xml)

Thank you

---

### Post by QIII on 2013-07-16
Ah!

There is a much, much easier way of doing that, and it is tailored to Ubuntu!  Someone has done all the work for us.

Give [this]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html") a read.   Ask questions if anything doesn't make sense!  You are really only interested in the first three pink code boxes.

Best wishes.

---

### Post by mohsen12 on 2013-07-16
Thank you guys

---

