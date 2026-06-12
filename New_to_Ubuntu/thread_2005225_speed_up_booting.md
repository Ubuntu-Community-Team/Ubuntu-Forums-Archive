---
title: "speed up booting"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by lenypl on 2012-06-17
after upgrading to 12.04 booting become very slow.how can i speed it up please help. i have a samsung laptop with intel core  duo processor.and 2gb ram.

---

### Post by fantab on 2012-06-17
Sometimes this can be due to all the junk accumulated in the System overtime. Install bleachbit and clean up your system. There are two modes, Normal and Bleachbit as root.
It can be installed from Software Center, or From Terminal:

```
sudo apt-get update
sudo apt-get install bleachbit
```

To run beachbit as root:
```
sudo bleachbit
```

or 

You can use Computer Janitor which comes as a part of Ubuntu Tweak Tool.

Also Check STARTUP APPLICATIONS to disable any application/services that are starting loading at system boot. You can disable them by unchecking the application/process.

---

### Post by lenypl on 2012-06-20
thank you friend. it works

---

### Post by upjeeper on 2012-06-24
> **fantab said:**
> Sometimes this can be due to all the junk accumulated in the System overtime. Install bleachbit and clean up your system. There are two modes, Normal and Bleachbit as root.
It can be installed from Software Center, or From Terminal:

```
sudo apt-get update
sudo apt-get install bleachbit
```

To run beachbit as root:
```
sudo bleachbit
```

or 

You can use Computer Janitor which comes as a part of Ubuntu Tweak Tool.

Also Check STARTUP APPLICATIONS to disable any application/services that are starting loading at system boot. You can disable them by unchecking the application/process.

hi Fantab - why do you run the "rudo apt-get update" first? is that just to be sure all updates are current before doing an install of a new program?

thanks!

---

### Post by Fernhill Linux Project on 2012-06-24
@ upjeeper

That's right, "sudo apt-get update" updates the package repositories so you are installing the latest updated version.

---

