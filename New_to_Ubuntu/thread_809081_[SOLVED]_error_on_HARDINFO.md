---
title: "[SOLVED] error on HARDINFO"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by nantax on 2008-05-27
I recently installed HARDINFO and there was an error message when you try to run it.

Warning

Cannot load ZLib. /usr/lib/libz.so not found".

I arrived at this [thread]("https://bugs.launchpad.net/ubuntu/gutsy/+source/hardinfo/+bug/178267") and tried to run:

$ sudo ln -s /usr/lib/libz.so.1 /usr/lib/libz.so

Now the error became:

Warning

Cannot load ZLib: /usr/lib/libz.so: cannot open shared object file: Too many levels of symbolic links

What do I do now?

---

### Post by ibutho on 2008-05-27
What is the output of running Applications -> Terminal
```
sudo find /usr/lib/ -name "libz*"
```

---

### Post by nantax on 2008-05-27
Thank you very much for your speedy reply ibutho.

This is the output:

```
nante@ubuntu:~$ sudo find /usr/lib/ -name "libz*"
[sudo] password for nante: 
/usr/lib/libz.so.1.2.3.3
/usr/lib/libzephyr.so.3
/usr/lib/libz.so
/usr/lib/libz.so.1
/usr/lib/compiz/libzoom.so
/usr/lib/libzephyr.so.3.0.0
/usr/lib/purple-2/libzephyr.so
nante@ubuntu:~$

```

---

### Post by ibutho on 2008-05-27
Try the following
```
sudo rm /usr/lib/libz.so
sudo ln -s /usr/lib/libz.so.1.2.3.3 /usr/lib/libz.so
```

---

### Post by nantax on 2008-05-27
Wow. That did the trick. Thanks again ibutho... I'm new to Ubuntu (although I have installed it a few times before) and I really appreciate your help. =D>

---

### Post by Dreamerman on 2008-08-23
> **ibutho said:**
> Try the following
```
sudo rm /usr/lib/libz.so
sudo ln -s /usr/lib/libz.so.1.2.3.3 /usr/lib/libz.so
```

Hi. Mine's slightly different. I don't have libz.so. Can I still use your commands ?

master@master-server:~$ sudo find /usr/lib/ -name "libz*"
[sudo] password for master: 
/usr/lib/purple-2/libzephyr.so
/usr/lib/libzephyr.so.3.0.0
/usr/lib/libz.so.1
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libzip.so
/usr/lib/libzephyr.so.3
/usr/lib/libz.so.1.2.3.3
/usr/lib/compiz/libzoom.so
master@master-server:~$

---

