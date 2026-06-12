---
title: "libqt4 4.1.1 required"
date: 2009-11-02
forum: Packaging and Compiling Programs
---

### Post by waspbr on 2009-11-02
hello everyone, 

I am compiling this program and as it turns out it requires qt4 4.1.1 libraries, karmic has v. 4.5.* . Does anyone know how I can get around this? 

```
checking for Qt4 libraries >= 4.1.1... configure: error: You need Qt libraries >= 4.1.1

```

thanks in advance

---

### Post by SevenMachines on 2009-11-03
4.5 libraries should work for the configure script as far as I can see ( as they are greater than or equal to 4.1.1 ) Might be a case of the script not finding the headers
With libqt4-dev installed, look at 
$./configure --help
Theres usually an option to specify the location of the qt headers manually, might be worth a try

---

### Post by waspbr on 2009-11-04
thanks for the tip, I will look into it

---

