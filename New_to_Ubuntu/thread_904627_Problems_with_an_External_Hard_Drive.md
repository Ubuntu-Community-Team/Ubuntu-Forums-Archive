---
title: "Problems with an External Hard Drive"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by Typeface on 2008-08-29
I feel rather silly having to ask this question. I recently got a bigger hard drive for my laptop, easy i thought i'll just clone it to my external hard drive with an Ubuntu live cd and then copy it back to the new hard drive. I had looked up the commands i need to know ( i was going to use sudo dd if= drive that wants copying of= were its going to be copyed to ). All i needed to do was delete what was on my external hard drive, however i dont have permission to edit anything on there and im not sure how to change this please could you help me.

---

### Post by cariboo on 2008-08-29
If you want to acces your external drive, change the permissions of the mount point:

```
sudo chmod -R 777 /media/<external_drive>
```

This is asumming that your external is mounted on /media and whatever the directory name of your mount point is.

Jim

---

