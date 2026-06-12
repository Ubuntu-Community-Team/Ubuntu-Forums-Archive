---
title: "Remove read only files."
date: 2008-10-30
forum: New to Ubuntu
---

### Post by theamber on 2008-10-30
Hi, I have installed Vuze and I tried t remove it but it was not listed so I went to the directory and I removed some files but others are read only and I can't remove with rm how can I change the attribute or remove them. 
Thanks.

---

### Post by cheetaux on 2008-10-30
If the file, for example, is named file.txt, you change remove the read-only permission (add write permission) by executing:

chmod u+w file.txt  (this gives the user write permission to the file)

---

### Post by theamber on 2008-10-31
> **cheetaux said:**
> If the file, for example, is named file.txt, you change remove the read-only permission (add write permission) by executing:

chmod u+w file.txt  (this gives the user write permission to the file)
Thanks I tried that and it said not permitted operation.

---

### Post by aramadia on 2008-10-31
To do things requiring more "permission" try adding the sudo command in front.

so...
sudo chmod u+w file.txt
or really you need to simply delete:
**sudo rm file.txt**

---

### Post by cheetaux on 2008-10-31
It could be that root owns the file, rather than you.  If so, you can use "sudo"  (do as super-user) to delete the file:

```
sudo rm -f filename
```

Sudo will ask you to enter your password.

---

### Post by theamber on 2008-10-31
Yes the sudo in front WORKS! but how can I remove directories with one command with files and subdirectories inside.

---

### Post by aramadia on 2008-10-31
**sudo rm -R name_of_dir**
The R stands for recursive.

---

### Post by ratmandall on 2008-10-31
> **theamber said:**
> Yes the sudo in front WORKS! but how can I remove directories with one command with files and subdirectories inside.

```
sudo rm -rf directory
```

---

