---
title: "[SOLVED] Moving all files from 1 folder to another"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by niiklas on 2008-12-02
Is there any way to move all files of a folder to another folder?

---

### Post by sharks on 2008-12-02
Just copy the folder and paste it anywhere......

Right click the folder and select copy and paste it where u want....

---

### Post by Paqman on 2008-12-02
One important point: each user only has ownership of the folders within their /home folder. If you want to transfer files to a location outside of your /home, you'll need to take on root privileges temporarily.

To do this prefix your CLI move or copy command with sudo, or else open the file browser with Alt-F2 and:
```

gksu nautilus

```

---

### Post by sharks on 2008-12-02
> **Paqman said:**
> 
To do this prefix your CLI move or copy command with sudo, or else open the file browser with Alt-F2 and:
```

gksu nautilus

```

And just dont forget to close the nautilus after u have finished editing...

---

### Post by binbash on 2008-12-02
mv /home/asdasd/asdasdsa/* /home/asdaaasd/asdasdasd/

---

### Post by niiklas on 2008-12-02
> **binbash said:**
> mv /home/asdasd/asdasdsa/* /home/asdaaasd/asdasdasd/

ok il try this since i guess the other answers are for ubuntu with gui

---

### Post by sharks on 2008-12-02
Open terminal and then :
To move:
mv /home/nameofthefolder /destination

To copy:
cp /home/nameofthefolder /destination

---

### Post by linux_tech on 2008-12-02
mv can move or rename files or directories
```
mv directory1 directory2
```
syntax is from to or source to destination

---

