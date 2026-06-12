---
title: "[SOLVED] Hardy Share folder"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by hobo on 2008-06-17
I can't seem to figure out how to share a folder with another user on my system. hardy 8.4 amd64. Any ideas?

---

### Post by BennBuntu on 2008-06-17
don't need file sharing setup, just use permissions system.
right click on the folder and choose properties, then permissions tab.
There you can choose to make the folder read and or writable to others. If you want you can also create a group (system >> users and groups).

You will also have to apply those permissions to the files inside, should be a box to tick, otherwise chmod in command line.
finally you can create a link to that folder and put it in their home directory or wherever. right click 'make link' or the ln function in command line.

---

### Post by freduardo on 2008-06-17
If you're talking about sharing a folder and its contents with another user on the same operating system, you just have to make sure to set the permissions on said folder right. 

E.g. You, user A, want to allow user B read and write access to /media/data.
There's few ways to go about this:

- The dirty way is to allow everyone read and write access by chmod -R 777'ing the folder.

- A cleaner way would be to make A and B a part of the same group and then allowing read and write access to the folder only for that group.

EDIT: Bennbuntu beat me to it.
Note to self: Type faster!

---

### Post by hobo on 2008-06-17
(solved) Thanks. I was right clicking the folder on the wrong screen and properties was greyed-out.

---

### Post by BennBuntu on 2008-06-17
One trick you might find handy,

open a terminal and type 

```
gksudo nautilus
```

nautilus is the file browser program. gksudo will launch it with root privileges so you have full access to both users files/folders.
The user that runs the command has to have adminstrative rights, so your primary user can do it, but if you've made a new user, you might have to change their settings in users & groups.

Only use it when you need it :)

---

