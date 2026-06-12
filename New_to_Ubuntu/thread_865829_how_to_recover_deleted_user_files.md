---
title: "how to recover deleted user files?"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by space-litter on 2008-07-21
long story short, i had multiple users and deleted a user profile without realizing that said profile had irreplaceable pictures saved on it. now i cannot access them. i have since recreated the profile to no effect. how can i recover the files from the previous user profile of the same name? i have root access.

---

### Post by t0p on 2008-07-21
Did you just delete the user's account in Users and Groups?  Or did you go and delete the user's home directory too?

If you just deleted the user's account, you should be able to access that old user's files.  In a terminal type

```
gksudo
```

A Run box will appear.  Type nautilus in the box.  A file manager window will appear. Navigate into the file system, into the /home directory.  There you'll see the home directories of all your users.  Go into the one that belongs to your old user and the files should be there.

If, however, you deleted the old user's home directory when you deleted his account, I think you've lost the files forever.  Unless you deleted it in Nautilus and it's still in the Trash bin.

---

### Post by space-litter on 2008-07-21
i wiped out everything, directories and all...and ive cleared the trash at least 3 times since then :(

edit: and i have since made a new user with the same name...does that preclude getting them in another dir?

---

### Post by Locutus_of_Borg on 2008-07-21
try an app called magicrescue

it is for recovering deleted files from the blocks that are still left

might work

---

### Post by t0p on 2008-07-21
> **space-litter said:**
> i wiped out everything, directories and all...and ive cleared the trash at least 3 times since then :(

edit: and i have since made a new user with the same name...does that preclude getting them in another dir?

Whether you'd made that new user or not, I think you've lost those files forever.  A forensic scientist would be able to retrieve them, but I don't think anyone here will be able to help you!

**EDIT:** Don't listen to me, listen to the Borg!  **magicrescue** is in the repos, and by its description it does seem rather magic!

---

### Post by Sef on 2008-07-21
> Whether you'd made that new user or not, I think you've lost those files forever. A forensic scientist would be able to retrieve them, but I don't think anyone here will be able to help you!

Files are not lost until they are written over.  And even then sometimes, they can be recovered.

---

### Post by zipperback on 2008-07-21
A quick check in google for:  deleted file recovery + linux

It appears there are 317,000 pages in google which come up using the above query.

Here is the link to the search I just did.

[http://www.google.com/search?hl=en&q=deleted+file+recovery+%2B+linux&btnG=Google+Search](http://www.google.com/search?hl=en&q=deleted+file+recovery+%2B+linux&btnG=Google+Search)

Hopefully this helps you.

- zipperback
:popcorn:

---

