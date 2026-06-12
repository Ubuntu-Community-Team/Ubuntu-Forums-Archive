---
title: "[SOLVED] Making a script executable"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by RussW210 on 2008-09-10
Hey guys, I am trying to create a uTorrent executable script.  My instructions were to type "sudo chmod a x /usr/bin/utorrent" to make the script executable (the shell script is correctly in the folder) but "a" is not an option for chmod.  Does anyone know how I can make this script executable?

---

### Post by sisco311 on 2008-09-10
```
sudo chmod a+x /usr/bin/utorrent
```

---

### Post by checkit on 2008-09-10
Find the file in Nautilus, right click on the file, go to Properties --> Permissions --> Execute (Allow executing file as a program).

---

### Post by RussW210 on 2008-09-10
Ahh, he was one off... thank you sisco.

That is another good way, thank you checkit.

---

### Post by sisco311 on 2008-09-10
> **checkit said:**
> Find the file in Nautilus, right click on the file, go to Properties --> Permissions --> Execute (Allow executing file as a program).
if the file is owned by root, then you must to run nautilus as root:
```
gksu nautilus
```

---

