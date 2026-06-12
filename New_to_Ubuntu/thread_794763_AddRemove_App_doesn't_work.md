---
title: "Add/Remove App doesn't work"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Cephaus on 2008-05-14
Im trying to install Azuerus, but every time I try to install it the app just freezes

Any help?

---

### Post by will1911a1 on 2008-05-14
Tried using sudo apt-get install from the terminal?

---

### Post by SunnyRabbiera on 2008-05-14
also there is synaptic too, a more advanced package tool then add/remove

---

### Post by Cephaus on 2008-05-14
But is there a way to fix it?

---

### Post by JimmyHopkins on 2008-05-14
If I'm not mistaken, Azuerus uses java, correct? I had problems running frostwire (which also uses java). Go to system -> admin -> synaptic package manager, search for "jdk", and remove any package with "jdk" in it's name, such as "openjdk" or "free-java-jdk". After removing this, try Azuerus.
For me, this got frostwire to run. It works because you probably have two different versions of java installed.

---

### Post by forrestcupp on 2008-05-14
> **JimmyHopkins said:**
> If I'm not mistaken, Azuerus uses java, correct? I had problems running frostwire (which also uses java). Go to system -> admin -> synaptic package manager, search for "jdk", and remove any package with "jdk" in it's name, such as "openjdk" or "free-java-jdk". After removing this, try Azuerus.
For me, this got frostwire to run. It works because you probably have two different versions of java installed.

Thanks.  That info helped me get Iriverter working.

---

### Post by aikiwolfie on 2008-12-28
You can fix this by reinstalling gnome-app-install using either Synaptic or apt-get.

---

