---
title: "ATI Radeon 9200 drivers"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by _Silver on 2008-05-30
Hi to all, I'm new in ubuntu and trying to install ati radeon 9200 drivers. I download drivers from [www.ati.com](www.ati.com). Driver name is ati-driver-installer-8.28.8.run and my question is with what program i can "run" run file? Ty in advice and sorry for my not very good English.

---

### Post by robertchahine on 2008-05-30
go to the system pannel>administrator>hardware drivers.
then tick the ati driver, it should ask you if you want to download and install the driver.and the ubuntu update manager will start the download
hope this will help

---

### Post by _Silver on 2008-05-30
I go to the panel System > Administration > Hardware drivers, but there are no components. No proprietary drivers are in use on this system.

---

### Post by robertchahine on 2008-05-30
hope this will help.

go to the terminal then 
```

sudo dpkg-reconfigure xserver-xorg

```
,you should give this a look maybe it will help

[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

### Post by shae on 2008-05-30
That version of fglrx will not compile against the modern kernel.  You will need to compile the 2.6.18 kernel and then compile the driver or you can continue to use the open source drivers.

---

