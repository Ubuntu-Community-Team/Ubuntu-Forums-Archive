---
title: "unexpected directory behavior"
date: 2018-01-07
forum: New to Ubuntu
---

### Post by craigdogg on 2018-01-07
not sure why I am unable to access the html folder.  I have the permission.  it's listed as a directory, but ubuntu insists there is no html directory/

```
root@restful-api:~/www# ls -la
total 12
drwxr-xr-x 3 root root 4096 Jan  7 19:36 .
drwx------ 5 root root 4096 Jan  7 19:32 ..
drwxr-xr-x 5 root root 4096 Jan  7 19:25 html
root@restful-api:~/www# cd html
-bash: cd: html: No such file or directory
root@mosaic-restful-api:~/www# whoami
root
```


thanks in advanced

---

### Post by Holger_Gehrke on 2018-01-07
The only explanation I can come up with for this behaviour of the shell: there is no directory named 'html'. But there is a directory named 'html ' (notice the difference ? There's a space at the end ... ) Try using command line completion; type 'cd h' and hit the tabulator key. It should complete the directory name for you. If there is some unusual character in the directory-name the completion will probably contain some kind of escape, for example '\ '.

Holger

---

