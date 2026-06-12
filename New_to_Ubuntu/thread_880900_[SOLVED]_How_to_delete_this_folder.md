---
title: "[SOLVED] How to delete this folder??"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by vikasmk on 2008-08-05
```
vikasmk@ubuntu:/home$ ls
guest  vikasmk  vikasmkk
```

 I created the vikasmkk folder as sudo . now i cant delete it .

```
vikasmk@ubuntu:/home$ sudo rm vikasmkk
[sudo] password for vikasmk: 
rm: cannot remove `vikasmkk': Is a directory

```
 
 SO how do i remove it???? :confused:

---

### Post by finer recliner on 2008-08-05
use either of these commands to delete a directory:

```
rmdir <directory>
``` or ```
rm -r <directory>
```

---

### Post by Yannick Le Saint kyncani on 2008-08-05
sudo rm -rf dontscrewthedirectoryname

---

### Post by finer recliner on 2008-08-05
(oops double post)

---

### Post by jerome1232 on 2008-08-05
when deleting a directory you have to add the -r option to rm. so that it recurses down into the directory and removes everything else. WARNING you won't be able to recover these files once you delete them so I would at least run it like this
```
sudo rm -rvI [directory]
```
double check the command, it will ask you if you are sure, if all look good say yes, then it will print the files it's removing so you have visual confirmation of whats going on.
but this will work too.
```
sudo rm -r [directory]
```

---

