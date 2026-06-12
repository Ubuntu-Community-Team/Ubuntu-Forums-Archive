---
title: "[SOLVED] Synaptic package manager"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by EvanRogers on 2008-10-02
Hello all, I have a problem.

When i try to start Synaptic Package Manager i get this error 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


So i opened a Terminal and put in Dpkg --configure -a and pushed enter, then it says: Requested operation requires superuser privilege

I do not know what i am doing wrong, i am the administrator\owner of this computer. I am very new at Ubuntu but please bear with me. Any help would be appreciated.

---

### Post by nachomania on 2008-10-02
Don't use a capital D, "sudo dpkg --configure -a" will work. It'll ask you for your password, and it'll go. Make sure to use small and capital letters where told to!

---

### Post by bobnutfield on 2008-10-02
> sudo dpkg --configure -a

Just enter your password.

---

### Post by EvanRogers on 2008-10-02
EDIT: Ok sorry i just wasn't entering sudo before i entered the rest, what does sudo mean? thanks guys.

---

### Post by bobnutfield on 2008-10-02
Did you type sudo before the command?

---

### Post by kansasnoob on 2008-10-02
> **EvanRogers said:**
> EDIT: Ok sorry i just wasn't entering sudo before i entered the rest, what does sudo mean? thanks guys.

pseudo root privilege - then it asks for your password

---

### Post by Ryadt on 2008-10-02
> **EvanRogers said:**
> EDIT: Ok sorry i just wasn't entering sudo before i entered the rest, what does sudo mean? thanks guys.
sudo means Super User DO. It gives you administrative privilege.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by darisk on 2008-10-02
(original post moved here: [http://ubuntuforums.org/showthread.php?p=5897714](http://ubuntuforums.org/showthread.php?p=5897714))

---

