---
title: "delete non-empty directory owned by root"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by ecs_pf5 on 2008-05-02
I have a non-empty directory on my Desktop which contains subfolders & files

/Desktop/AdobeReader_enu-8.1.2/[stuff]/?

it is owned by root

How can I delete /AdobeReader_enu-8.1.2/ by using the terminal?

---

### Post by frup on 2008-05-02
sudo rm -Rf /directory

-R = recurrsive (files inside)
-f = force
rm = remove
sudo = root

---

### Post by ecs_pf5 on 2008-05-02
Thanks, I was trying rmdir.. folder now gone :)

---

### Post by nejode on 2008-05-02
In the terminal:

sudo rm -R /home/*username*/Desktop/AdobeReader_enu-8.1.2

In the GUI:

ALT+F2>> kdesu konqueror>> you get konqueror with root rights (KDE)
ALT+F2>> gksudo nautilus>> nautilus with root capabilities (gnome)

---

### Post by zaussome on 2008-05-03
z

---

