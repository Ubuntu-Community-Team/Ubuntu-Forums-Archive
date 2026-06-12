---
title: "copying whole folder in terminal"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by ja660k on 2008-09-20
hey guys, 
in my /var/www/ i cant copy anything by drag/drop i have to zip the folder and sudo mv the zipped folder, but i dont know how to unzip the folder, 

or better yet copy the whole folder, so i dont need to zip it in the first place?

thanks

---

### Post by k33bz on 2008-09-20
if you want to copy the folder and all of its contents

```
sudo cp -R /path/to/where/folder/at /path/to/where/you/want/folder
```

---

### Post by mc4100 on 2008-09-20
If you want drag & drop for /var, you're going to need to run the File Manager with root privileges:
```
gksudo nautilus
```
And put in you're password. Drag & drop will now work, caution in advised.

---

### Post by ja660k on 2008-09-20
thanks =)

---

