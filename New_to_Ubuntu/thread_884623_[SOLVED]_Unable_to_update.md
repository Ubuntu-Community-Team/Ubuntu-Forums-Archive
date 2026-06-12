---
title: "[SOLVED] Unable to update"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Al B on 2008-08-09
On trying to update Kubuntu (Dapper) I get the following error message following sudo apt-get update

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

How can I fix this error ?

---

### Post by Elfy on 2008-08-09
Try this

```
cd /var/lib/dpkg
sudo mv status status-bad
sudo cp status-old status
sudo apt-get update
```

---

### Post by Al B on 2008-08-09
Thanks a lot forestpixie. That has solved that problem. Now for more problems, I am going to try and upgrade to Hardy.

---

