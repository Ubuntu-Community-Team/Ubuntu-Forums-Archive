---
title: "Apply Permissions To Enclosed Files"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by expatCM on 2012-04-07
I have just transferred over some hidden directories to my new /home.  These are configuration files and databases.  When launched the related program will not run since the transferred settings are root / root rather than user / group.

So I thought I would use nautilus to fix this.  Started nautilus (sudo nautilus) and then changed the user and group for the directory.  I then clicked on "Apply Permissions To Enclosed Files" and the border turned red round the dialogue.  I then waited, had a coffee and came back. Clicked on the Close button and the window closed.   The permissions of the enclosed files have sadly not changed.   Does anyone know what I have done wrong?

---

### Post by papibe on 2012-04-07
Hi expatCM.

Rather than a permissions problem you have an ownership problem. You can easily take back the ownership of those files by running:
```
sudo chown -R youruser:youruser .*
```
(replace 'youruser' with your actual username).

Hope that helps.
Regards.

---

### Post by expatCM on 2012-04-07
Yes, you are right ...  my clumsy use of terminology.

---

