---
title: "Full remove Apache"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Zeck on 2008-05-08
Hi all,
I try to remove apache. But it not removed. How can I remove apache on my pc. Any Idea ?

---

### Post by tamoneya on 2008-05-08
```
sudo apt-get remove --purge apache2
```

---

### Post by Zeck on 2008-05-08
Thanks lot.
I want to know how to install manual apache. I download apache then how to manual install it on my pc. And how to change my apache webroot( /var/www ) Any Idea ?

---

### Post by Zeck on 2008-05-08
I trying install program using terminal. But it have a problem. Here is the problem.

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

---

### Post by kesman on 2008-05-08
So did you try to run the given command?
```

sudo dpkg --configure -a

```

---

### Post by tamoneya on 2008-05-08
just do what it says.  Just remember you will need root permissions
```
sudo dpkg --configure -a
```

---

### Post by tamoneya on 2008-05-08
again search the forums and I quickly found several threads solving your problem.

[http://ubuntuforums.org/showthread.php?t=18964](http://ubuntuforums.org/showthread.php?t=18964)
[http://ubuntuforums.org/showthread.php?t=570842&highlight=%2Fvar%2Fwww](http://ubuntuforums.org/showthread.php?t=570842&highlight=%2Fvar%2Fwww)

if both of those fail let us know what you tried and what your errors were.

---

### Post by hyper_ch on 2008-05-08
as told before, you should use the repos normally... especially when you start interlinking stuff like a LAMP environment...

---

### Post by Zeck on 2008-05-08
> **hyper_ch said:**
> as told before, you should use the repos normally... especially when you start interlinking stuff like a LAMP environment...

How to repos normally ? Could you teach me step by step ?

---

### Post by hyper_ch on 2008-05-08
```

sudo apt-get install apache2 mysql php5 .......

```

---

