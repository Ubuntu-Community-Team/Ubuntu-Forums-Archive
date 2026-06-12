---
title: "Restoring backup"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by shoaibi on 2008-05-30
i have a home.tbz file which is actually a tarbar of a user say alpha1 on my previous ubuntu installation. What i wanna do is that i wanna have that user back with all his settings and all that. Should i do this:

1. create new user alpha1 [currently i have only root account]
2. extract the tbz file content and replace it into the new user's home dir

or what? will there be some permissions problem? 
What if the uid of previous aplha1 was 1001, and this one becomes 1002? or what is its the same?

---

### Post by quelx on 2008-05-30
if the **uid** changes simply **chown** the files back to the user

**sudo chown username:username -R /home/alpha1**

where **username** is the original user, tar preserves file ownership (if you tell it to) so that really shouldn't be an issue

from **man tar**

```
      -o, --no-same-owner
              extract  files  with  owner set to current user (the default for
              non-root users)
```

---

