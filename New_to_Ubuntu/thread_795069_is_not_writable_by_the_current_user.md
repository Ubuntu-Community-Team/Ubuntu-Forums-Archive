---
title: "is not writable by the current user"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by appoloin on 2008-05-15
Hi guys,

i finally got figure out how to install planeshift now i hit another hurdle
i attach the screenshot. can anyone tell me how i can fix this please?

---

### Post by drs305 on 2008-05-15
> **appoloin said:**
> Hi guys,

i finally got figure out how to install planeshift now i hit another hurdle
i attach the screenshot. can anyone tell me how i can fix this please?

One method is to change the owner of the usr/local/games folder to you if you are the only one who is going to access it, or to a group (where the :group comes in).

```
sudo chown -R username:group /usr/local/games
```

---

### Post by nicedude on 2008-05-15
You need to give yourself write permission on that directory. You can do that a number of ways but try running this "man chown" without quotes to read the manual page on the chown command which allows you to take ownership of directories and files. Hope this helps you out man.

---

