---
title: "installing software from .tar.gz"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by energy. on 2008-07-26
I have super_pi.tar.gz and I am not quite sure what to do with it :confused:

---

### Post by Xerp on 2008-07-26
Normally:

```

tar -zxvf file.tar.gz
cd directoryname
./configure
make
make install

```

Reading the README file in the archive is also suggested :)

---

### Post by braddcadd on 2008-07-26
A tar.gz file is like a *.zip file.  You have to extract it first.  What you do next is probably in some README file or something.

```

tar -xvvzf bla_bla.tar.gz

```

For more information:
```

man tar

```

---

### Post by InfinityCircuit on 2008-07-26
super_pi is a binary.  If you just extract it using file-roller or the above commands there will be an executable inside.  You will want to read the README and then open a terminal and execute it. by navigating to the directory and executing ./name-of-exec.

---

### Post by spiderbatdad on 2008-07-26
dont forget to make it executable
```
sudo chmod +x name_of_file.sh
```

---

### Post by SunnyRabbiera on 2008-07-26
Just remember, you may not have to go to site a, site b and site c like you do in windows to obtain software.
In Ubuntu packages are made available though something called repositories, repositories are a library of the most common applications you may need to get things working.
If you are unsure on installing things in ubuntu use this guide:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by energy. on 2008-07-26
> **SunnyRabbiera said:**
> Just remember, you may not have to go to site a, site b and site c like you do in windows to obtain software.
In Ubuntu packages are made available though something called repositories, repositories are a library of the most common applications you may need to get things working.
If you are unsure on installing things in ubuntu use this guide:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

this software isn't included in the repositories.

---

### Post by SunnyRabbiera on 2008-07-26
still its usually wise to stick to the repositories.
If the application is so important to you make sure you can at least dig up a .rpm installer and use alien to convert it.
Also make sure to enable extra repositories too if needed, installing from source is not a good idea for beginners.

---

