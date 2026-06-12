---
title: "Why is the group of my file changing when I move it?"
date: 2016-06-25
forum: New to Ubuntu
---

### Post by Nutellaeis on 2016-06-25
I am probably missing something very basic here so maybe someone can help:

I have a file that I want do move from one folder to another. The file is created by the user **jd **and the group **download**. I work as the user **maximilian**. **maximilian** has the primary group **maximilian** and also is in the groups **download** and ** media**. So I use the following commands:

```

sudo chown maximilian:media file
chmod 660 file
mv file /new/folder

```

The destination folder is owned by **maximilian:media**
But after I move my file it is suddenly owned by **maximilian:maximilian**. 

But if I use 

```
sudo mv file /new/folder
```

the file stays owned by **maximilian:media**

Can someone explain me what is happening there? If I move a file owned by a user and group to a folder belonging to the same user and group should it not stay the same?

.

---

### Post by grahammechanical on 2016-06-25
> If I move a file owned by a user and group to a folder belonging to the same user and group should it not stay the same?

Yes, if you are working as that user. No, if you are prefixing the move command with sudo. You are in effect creating a new file owned by root.

---

### Post by Impavidus on 2016-06-25
Is the destination directory on the same partition as the source? If not, you're not moving the file, but creating a new file.

---

### Post by Nutellaeis on 2016-06-26
Yes the destination is on a different partition. So it creates a new file (therefore using the primary group) and deletes the old one? But why are the permissions preserved then? Seems a little inconsistent.

---

### Post by The Cog on 2016-06-26
What about yourself? Are you a member of the media group. If not, then I don't think you are allowed to create files that belong to that group.
Are you allowed to do **chgrp media /new/folder/file** after the move operation?

---

### Post by Nutellaeis on 2016-06-26
> **The Cog said:**
> What about yourself? Are you a member of the media group. If not, then I don't think you are allowed to create files that belong to that group.
Are you allowed to do **chgrp media /new/folder/file** after the move operation?

I am not. But I was so sure I added the user to the group :redface: . Sorry for that. Of course it can not work then.

---

