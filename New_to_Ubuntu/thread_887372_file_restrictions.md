---
title: "file restrictions"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by ellankavi on 2008-08-12
when i change the file permissions for restricted folders, the files inside them are still not accessible. they are still locked. i have to repeat the process of unlocking them :( Any suggestions?

---

### Post by Rossco_ on 2008-08-12
There should be a button at the bottom of the Right-Click > Properties > Permissions tab that says "Apply Permssions to Enclosed Files". If you click this, that should solve your problem.

---

### Post by ellankavi on 2008-08-12
tried that! not working :(

---

### Post by houbysoft.xf.cz on 2008-08-12
cd /path/to/your/folder
chown <yourusername> **

If it will not work, try sudo chown <yourusername> **.

Hope that helps.

---

### Post by aloshbennett on 2008-08-12
Throw in a -R too ;-)
(as long as you know what you are changing)

---

