---
title: "New folder not recognised in Terminal"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by asharpham on 2012-05-16
I've been looking at the instructions how to install a Sierra 320U USB modem on my  Ubuntu 12.04 machine but have run into a problem. As per the  instructions, I created a folder in "home" called "kernel-3.2.y". I then  extracted the files into that folder. This all worked well.


 When I try to move to the folder just created, I keep getting the  error message in Terminal "no such file or directory". I've repeatedly  checked my spelling and compared my command to the instructions and all  appears well. I've also checked that the folders and files actually  exist in my directory and they do.


 What am I doing wrong? Why are the folders not recognised when I try to move to them in Terminal?


 Alan

---

### Post by 2F4U on 2012-05-16
Provide the output of ls -al from your home folder and the command you use to copy the folder.

---

### Post by roelforg on 2012-05-16
I think he might've created a subfolder in /home instead of his homedir.
Run:
```

ls /home

```
if the folder's there:
It should be in /home/<username>
If you're working with a terminal you can use ~ as it expands to your homedir.

---

### Post by asharpham on 2012-05-17
Thanks so much guys. I got lost between "/home" and "/home/alan".

Alan.

---

