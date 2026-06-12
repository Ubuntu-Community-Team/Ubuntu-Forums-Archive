---
title: "[SOLVED] Cant install programs"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by etomic13 on 2008-08-03
Whenever I start synaptic or try to install something in add/remove I receive this error and it promptly closes the program 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by perlluver on 2008-08-03
> **etomic13 said:**
> Whenever I start synaptic or try to install something in add/remove I receive this error and it promptly closes the program 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

In a terminal run ```
sudo dpkg --configure -a
```.  That should sort it out for you.

---

### Post by cpetercarter on 2008-08-03
Appications > Accessories > Terminal
Enter:
```
sudo dpkg --configure -a
```
Enter your password at the prompt.

---

### Post by etomic13 on 2008-08-03
Ok I did and it says i have a broken package how should i uninstall it?

---

### Post by sayakb on 2008-08-03
Do:
```
sudo apt-get install -f
```

---

### Post by cpetercarter on 2008-08-03
Alternatively:
System > Administration > Synaptic Package manager
Enter you password at the prompt.
Edit > Fix broken packages

---

### Post by quinnten83 on 2008-08-03
If the broken packages can't be fixed, remove them and try to reinstall.
What were you trying to install. Usually java gives people trouble, because it opens an installation in the terminal and if you don't know this and you close the terminal, it breaks the installer.

---

### Post by robertchahine on 2008-08-03
i think the 
```

sudo apt-get install -f 
```
will fix the problem

---

### Post by etomic13 on 2008-08-03
Alright that fixed it, I believe it was the Java run time enviorment that did it I closed it out because it looked like it was hanging.

---

### Post by sayakb on 2008-08-03
If all your problems have been addressed to, please mark the thread as solved :)

---

