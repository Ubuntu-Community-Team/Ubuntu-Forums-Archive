---
title: "Enter Samba shares by the Terminal"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Fixman on 2008-07-30
I got a windows computer witch I'm sharing with Samba, and it works perfectly. The only problem is that I must do a little automated task, so I would like to know if there was some way to access Samba-shared folders (shared from a windows computer to here) by the terminal.

---

### Post by bodhi.zazen on 2008-07-30
Yes, absolutely

You can manually mount the share 

sudo apt-get install smbfs

sudo mount -t cifs //server/share /mnt -o username=xxx,password=yyy

cd /mnt

---

### Post by Fixman on 2008-07-30
> **bodhi.zazen said:**
> Yes, absolutely

You can manually mount the share 

sudo apt-get install smbfs

sudo mount -t cifs //server/share /mnt -o username=xxx,password=yyy

cd /mnt

Great, thanks!

---

### Post by Fixman on 2008-07-30
By the way, I noted that if you use this method you can create/modify files using the terminal, but not using nautilus. Any way to remedy this?

---

### Post by bodhi.zazen on 2008-07-31
> **Fixman said:**
> By the way, I noted that if you use this method you can create/modify files using the terminal, but not using nautilus. Any way to remedy this?

Assuming the share is set rw on the server side,just add a few more options :

```
sudo mount -t cifs //server/share /mnt -o username=xxx,password=yyy,uid=1000,gid=100
```

The mount will now be owned by user 1000 (the first user in Ubuntu) and the group users. Feel free to adjust accordingly ...

---

