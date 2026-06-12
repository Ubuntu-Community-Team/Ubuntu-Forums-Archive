---
title: "[SOLVED] I need to copy my home folder to an external."
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Tom--d on 2008-05-20
I'm on the live CD at the moment and I need to copy my home folder, on the harddrive, to my external.

when I copy it, it comes up with errors saying cannot copy because you cannot read the file. (along those lines)

Same with root. I get those errors.

How can I copy mt home folder over?



Thanks,
tom

---

### Post by Joeb454 on 2008-05-20
I tend to copy it all, then when I get an error, try again without the folder specified. Works ok for me, though it gets a bit tiring to do :p

---

### Post by Tom--d on 2008-05-20
Ok,thank you.

Will give it a go now :)

---

### Post by Tom--d on 2008-05-20
mm.. some stuff still didn't copy :( 

It says basically I cannot read the file because I do not have permission :(

---

### Post by lswest on 2008-05-20
try tarring the folder (in nautilus show hidden folders, ctrl+a then right-click "create archive" and make it into a tar.gz) and then copy it over to the external drive and extract it.

If that also does not work can you post back the output of```
ls -l ~
```

---

### Post by Tom--d on 2008-05-20
It working now :)

It was my fault.. I didn't see the option. 

As root in nautilus.. i right clicked my home folder and changethe permission to root and everything in that folder to root :D 

Now it copying..

Thanks :)

---

### Post by lswest on 2008-05-20
> **Tom--d said:**
> It working now :)

It was my fault.. I didn't see the option. 

As root in nautilus.. i right clicked my home folder and changethe permission to root and everything in that folder to root :D 

Now it copying..

Thanks :)

Make sure you change the permissions back to the right user, or else everything will be messed up.

---

### Post by Tom--d on 2008-05-20
> **lswest said:**
> Make sure you change the permissions back to the right user, or else everything will be messed up.



For some reason.. I didn't need to. 

All my files are in my permission. (I never touched them. Just copied them over.)

---

