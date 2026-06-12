---
title: "couple of problems,permission denied"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-11
maybe i forgot how to access /etc/fstab but when i do i get permission denied even as root???also last night a new 76.9 media appeared in my
places tap and its the same as file system is this aproblem??

rick

---

### Post by quantumstitch on 2008-07-11
can you
```

ls -l /etc/fstab

```
if permissions are messed up,
```

sudo chmod 655 /etc/fstab

```
and
```

sudo pico /etc/fstab

```
to edit.

---

### Post by Cypher on 2008-07-11
How are you opening the /etc/fstab file for editing. If from the command line, are you doing "sudo <editor> /etc/fstab" or going through the file manager?

Show us the output of
```

ls -l /etc/fstab

```

---

### Post by Inxsible on 2008-07-11
When you say a new partition appeared ... - now I would love that getting extra space magically for free ;)

Seriously, did you muck around with the fstab prior to this? change some settings or even use Gparted to create/delete some partitions?

---

### Post by rixtr66 on 2008-07-11
rick@rick-laptop:~$ ls -l /etc/fstab
-rw-r-xr-x 1 root root 1279 2008-07-11 10:18 /etc/fstab
rick@rick-laptop:~$ 
im not sure what i did i was messing around with the command line and the
storage device mgr.and it suddenly appeared.is thi s harmful or isit ok??

---

### Post by rixtr66 on 2008-07-11
i wasnt sure of the right command to get into /etc/fstab but the command you gave me with pico worked,i wanted to see if my memory stick and my psp
were rgistering at first they wouldnt auto mount or you couldnt add to the media without going through nautilus,but i think i fixed that,the only problem i have now is i cant get rid of whats on the memory stick,how can i erase it or remove files??
rick:confused:

---

