---
title: "File transfer btwn users"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by waterrr on 2008-07-24
I have 2 users, admin and user1. I would like to transfer some of the files from admin onto user1 so that I am able to view it via SSH when logging in as user1 - how can I transfer some of the files that I want from admin onto user1?

thanks for the help!):P

---

### Post by anotherdisciple on 2008-07-24
well if you just want to MOVE the files you would open the terminal and do this...

```
sudo mv /home/admin/path/to/files /home/user1/new/path
```

If you want to share those files... you have to change their permissions... you add a user group and put admin and user1 in it. then you do this to the files....

```
chmod 775 /home/admin/path/to/files
```

you should know what 775 does... it makes it able to read/write and execute by the user and group... but only read and execute by others... you may want the user group to only read/execute... if so... let me know...

---

