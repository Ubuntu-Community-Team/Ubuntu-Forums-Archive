---
title: "Documents files lost after an update"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by josefalarka on 2013-07-10
Good day! My files in Documents and Downloads folders have been lost after doing ubuntu update. I am using ubuntu 12.10. How to recover back my lost files. And my desktop icons disappeared also. Any help is very much appreciated.

---

### Post by Snowhog on 2013-07-10
Obviously, that shouldn't have happened. You say you did an update. Are you sure, or did you 'upgrade' your Ubuntu by installing the newer version from a LiveUSB/DVD? If that is the case, and you told the installer to format your /home partition, then your stuff is toast.

---

### Post by josefalarka on 2013-07-10
Sorry I forgot to tell. After an update, I restarted my computer. When logged in, ubuntu prompt to do a partial upgrade. after successfully doing the partial upgrade and restarted my computer, the file on Documents folder disappeared. Is partial upgrade overwritten my existing settings?

---

### Post by Snowhog on 2013-07-13
We still need to know (you haven't actually said) what your mean by 'update'. You are now running 12.10. Were you running 12.04 before this 'update'? How did you update?

---

### Post by newb85 on 2013-07-13
If you did the upgrade while running Ubuntu from the Hard Drive, then your partition couldn't have been reformatted.

Open a terminal (by hitting Ctrl+Alt+T), enter the following commands one-at-a-time, hitting enter after each one.

```
ls -al | grep *ocumen*
ls -al | grep *eskto*
ls -al | grep *ownlo*
```

Post the results of each.

---

