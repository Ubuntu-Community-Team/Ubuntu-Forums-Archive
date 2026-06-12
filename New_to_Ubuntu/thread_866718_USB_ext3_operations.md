---
title: "USB ext3 operations"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by ra2008 on 2008-07-22
Hi,
i have formatted my USB memory to ext3,
and i cant paste any files to it using the mouse, only by command line?
y?
Thanks

---

### Post by kdb424 on 2008-07-22
when you move files to it by command line, do you use sudo?

---

### Post by ra2008 on 2008-07-22
> **kdb424 said:**
> when you move files to it by command line, do you use sudo?

yes ,,
i paste to it as root user

---

### Post by kdb424 on 2008-07-22
I don't think that the main account is root user unless you log in as root. Running as root is never recommended. You will need to set permissions so that all users can modify it, or possibly try another format, like FAT

---

### Post by Rhubarb on 2008-07-22
This is a simple user privileges issue.
If the usb drive gets mounted as /media/disk, you can enable your user to read / write to it without having to be root.
Where **username** = your user name:-
```
sudo chown -R **username** /media/disk/
sudo chgrp -R **username** /media/disk/
```

---

### Post by kdb424 on 2008-07-22
Thanks Rhubarb. That was what I was trying to say, but I didn't know how to give him an answer.

---

