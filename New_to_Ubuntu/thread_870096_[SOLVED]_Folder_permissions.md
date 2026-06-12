---
title: "[SOLVED] Folder permissions"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Kolmogorov on 2008-07-25
Hi,

I have copied some folders from my cd to my home folder. But when i try to change the name of these folders, ubuntu says that i can't do this because i'm not the owner...what can i do to change this ?

Thanks.

---

### Post by LowSky on 2008-07-25
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by pmlxuser on 2008-07-25
just do
```

$sudo chown <username>:<username>  <folder>

```
the folder can actually be your whole home ie

you could say for user john
```

$sudo chown john:john /home/john

```

or for specific files you could do the norms

```

$sudo chmod 777 filename 

```
[giving it for everyone to do as he please]

---

### Post by Kolmogorov on 2008-07-25
Thanks for the quick answer. But i have another one for you :). I have several folders in my /home/steeve/Pictures/ folder. How can i apply your command to change the owner permissions to all sub-folders and the files in it ?

Thanks !

---

### Post by GreenN00b on 2008-07-25
chmod and chown have an -R option to execute recursively. You can use something like this:

```
sudo chown -R john:john folder
sudo chmod -R 777 folder
```

---

### Post by t0p on 2008-07-25
Alternatively, if you want to do it in the GUI, open a Terminal and type in
```
gksudo
```

In the Run box that appears, type 
```
nautilus
```

In the file manager that appears, navigate to the files/directories you want to change.

---

