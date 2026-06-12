---
title: "Permissions issues in my home folder"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by das letzte einhorn on 2008-06-12
I have recovered some files from my USB key and have saved them to my home folder. However, it seems that the folder was not recognized as owned by me, therefore I had to copy the files using gksudo nautilus. This causes problems now because I cannot open the new files with my user account, despite trying to set read/write permissions to me while using gksudo nautilus, and also I receive an error message when I load Ubuntu which says that one default file (a .drmc file) is being ignored because there are two owners in my home folder

Any hints on how to solve this? Any code I need to provide?

Thanks!

---

### Post by ibutho on 2008-06-12
You can change the ownership of the files or directories using chown e.g.
```
sudo chown username:group somefile
```
To change the permissions recursively for a directory and its subdirectories
```
sudo chown -R username:group somedir
```

---

### Post by ad_267 on 2008-06-12
You can also do this by using gksudo nautilus again, browsing to the folder and right click - properties - permissions and change the owner to yourself and select apply permissions to enclosed files.

---

### Post by das letzte einhorn on 2008-06-12
@ad_267: I did try your solution, and for some odd reason it did not work. The ownership did not change. 

@ibutho: Yours did worked however. Thanks!

---

### Post by alienexplorers on 2008-06-12
Please mark your thread as solved by going to your first post and selecting thread tools and select mark as solved.

---

