---
title: "harddrive became read-only"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by Genjing on 2012-06-26
I have a toshiba external harddrive that I have been using to move photos between my Ubuntu 12.04 laptop and my mac. It has worked fine for month and then suddenly the other day Ubuntu started marking all my folders and files on the drive as read-only. They still seem fine on my mac. When I try to change the permissions on the drive I get this message: "Sorry, could not change the permissions of "PHOTOS": Error setting permissions: Read-only file system". Any idea what is causing this?

---

### Post by mapes12 on 2012-06-26
> Any idea what is causing this?If you just unplug the USB plug before selecting "Safely remove" (or whatever is called) then you stand a good chance of getting the permissions problem.

The only way I know how to fix it is to reformat it, but others may have a better solution.

EDIT: How about launching Nautilus with super user permissions ```
gksu nautilus
```then have another go at resetting the permissions.

---

### Post by vaah on 2012-06-26
whats the filesystem of your external harddrive?
have you tried "chown" then "chmod"?

---

### Post by ajgreeny on 2012-06-26
If the drive is ntfs, attach it to a windows machine but make sure you "Remove safely"; do not simply pull it out, as most windows users seem to do.  That may reset the drive properly.

---

