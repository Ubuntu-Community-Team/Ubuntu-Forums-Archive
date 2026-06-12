---
title: "XAMPP in my ubuntu 8.10"
date: 2009-03-12
forum: Programming Talk
---

### Post by binumathew on 2009-03-12
i installed the XAMPP in my ubuntu 8.10 sucessfully,but sir i cant able to copy any of the file to /opt/lampp/htdocs/ folder why this happening

i am a beginner in both PHP and Linux, can u explain me...plz....waiting for your response

---

### Post by Tibuda on 2009-03-12
You need to change that folder permissions. To do so you can:
1. Type this in the terminal```
sudo chown $USER:$USER /opt/lampp/htdocs/
```
or
2. Open nautilus as root (Alt+F2, gksu nautilus), go to /opt/lampp, right click htdocs folder and click properties. There's a "Permissions" tab in the dialog, and you'll be able to change the folder owner.

---

