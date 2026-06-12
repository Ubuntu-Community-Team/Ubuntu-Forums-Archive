---
title: "Create directory Permissions?"
date: 2014-06-11
forum: New to Ubuntu
---

### Post by dee7 on 2014-06-11
Xubuntu 14.04 Need to create directory /usr/share/foomatic/db/source/ at share create folder 'greyed out' . Permissions needed ? Was logged in as administrator . How to give myself permission to do this ?

---

### Post by KennethLarsen on 2014-06-11
You could try this in the terminal
> sudo mkdir /usr/share/foomatic/db/source/

---

### Post by deadflowr on 2014-06-11
What are the current permissions and ownerships?
```
ls -la <path-to-file>
```
(I'm too lazy to type the path, so replace path-to-file with the path)

In general, though to change permissions you can run something simply like
```
sudo chmod -R XXX path-to-folder
```
-R means recursive, and the XXX means permissions for owner,group, and other.
replace X with number 0, 1 ,2, 4, or 7.
0 = none 
1 = execute
2 = write
4 = read
7 = all
more here
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Hope it helps.

---

### Post by dee7 on 2014-06-11
Yes thanks sudo chmod etc worked + Thanks for the link And have installed files I needed for OKI printer but yet to actually print but am progressing slowly .

---

