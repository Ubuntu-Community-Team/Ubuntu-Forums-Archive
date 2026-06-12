---
title: "[SOLVED] Host folder in Wubi Install is missing."
date: 2008-06-12
forum: New to Ubuntu
---

### Post by steve101101 on 2008-06-12
After resizing my virtual disk with LVPM, the /host folder is no longer on the file system. I am not sure how this could have happened, but it did. Can someone please tell me how to restore this folder, becasue i use a lot of data still on the windows partition. 

Also the wubi install is still on the same disk as the windows install, just a bit larger.

---

### Post by steve101101 on 2008-06-13
Does anyone know the answer to this.

---

### Post by steve101101 on 2008-06-18
for me for some reason the folder was nolonger being mounted at login. 

to fix this enter the following code ...

```


sudo gedit /etc/fstab


```

then add the following line ...

```

/dev/**LOCATION OF HOST DRIVE**       /host   ntfs default 0       0

```

---

