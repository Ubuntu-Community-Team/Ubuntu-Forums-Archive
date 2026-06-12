---
title: "sshfs permission error"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by honeybear on 2012-03-15
Hello, I tried to mount to /mnt/sessy

```
# sshfs sessy@mycomputer:/home/sessy /mnt/sessy
```

however it displays: 

```
fuse: failed to open /dev/fuse: Permission denied
```

I would like to know how to give the permission to my user to do sshfs? what is the secured way, without giving the user too much permissions? 

thanks

---

### Post by matt_symes on 2012-03-17
Hi

> **honeybear said:**
> Hello, I tried to mount to /mnt/sessy

```
# sshfs sessy@mycomputer:/home/sessy /mnt/sessy
```

however it displays: 

```
fuse: failed to open /dev/fuse: Permission denied
```

I would like to know how to give the permission to my user to do sshfs? what is the secured way, without giving the user too much permissions? 

thanks

Try adding yourself to the group fuse.

Kind regards

---

