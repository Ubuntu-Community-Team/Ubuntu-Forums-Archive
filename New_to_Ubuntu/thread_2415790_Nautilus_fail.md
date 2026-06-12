---
title: "Nautilus fail"
date: 2019-03-31
forum: New to Ubuntu
---

### Post by hensobr on 2019-03-31
Nautilus doesn't allow copy files to another directory. I have set all the permissions as su. Help.

---

### Post by garye on 2019-03-31
Have you tried ```
sudo nautilus
```

---

### Post by Frogs Hair on 2019-03-31
Hello hensobr

Do not use sudo alone to open graphical applications as it can cause permission errors in the future. If needed use the following. You could also elaborate more on what you are trying to accomplish. ```
sudo -H nautilus 

```

---

### Post by yancek on 2019-03-31
You are posting at the Ubuntu forums so we all expect that you are using Ubuntu but we don't know which version/release so kindly post that.
Post the permissions/owner/group with the ls -l command on a directory you are trying to copy to.
Are you actually using 'su' to get permissions changed?  Ubuntu by default doesn't enable a separate root user so you would have had to set that up yourself.
The site below is the Ubuntu documentation on using sudo, advantages/disadvantage.  I would suggest you familiarize yourself with it.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by hensobr on 2019-04-03
Nautilus is now working normally.
Thanks

---

### Post by hensobr on 2019-04-03
Thanks

---

### Post by hensobr on 2019-04-03
The Ubuntu 18.04.2 LTS I use seems to work normally now.
Thanks

---

