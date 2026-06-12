---
title: "[SOLVED] Permission denied to symbolic lnk folder"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by rache1111 on 2008-08-21
Hi,

I am trying to access the Example folder in my home directory, which is a symbolic link linking to the /usr/share/example-content.

:~$ ls -l Examples
lrwxrwxrwx 1 sedi sedi 26 2008-08-20 12:58 Examples -> /usr/share/example-content

ls -ld /usr/share/example-content/
dr--r--r-- 3 root root 4096 2008-07-02 06:20 /usr/share/example-content/

but when I do
cd Examples
bash: cd: Examples: Permission denied

I am logged in as sedi, why am I getting the permission denied when the read permission is set to all users?

---

### Post by iaculallad on 2008-08-21
> **rache1111 said:**
> Hi,

I am trying to access the Example folder in my home directory, which is a symbolic link linking to the /usr/share/example-content.

:~$ ls -l Examples
lrwxrwxrwx 1 sedi sedi 26 2008-08-20 12:58 Examples -> /usr/share/example-content

ls -ld /usr/share/example-content/
dr--r--r-- 3 root root 4096 2008-07-02 06:20 /usr/share/example-content/

but when I do
cd Examples
bash: cd: Examples: Permission denied

I am logged in as sedi, why am I getting the permission denied when the read permission is set to all users?

What about doing:

```
cd ~/Examples
```

---

### Post by Vivaldi Gloria on 2008-08-21
You need the execute bit set (x) on a directory to be able to cd to it.

---

### Post by rache1111 on 2008-08-21
Thanks Gloria, that worked.

---

