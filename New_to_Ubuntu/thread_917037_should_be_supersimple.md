---
title: "should be supersimple"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-09-11
I need to change the permissions for a folder to read and write, but it says the owner is root and it wont let me change it so I can save files to the folder...how do i do this?

---

### Post by WRDN on 2008-09-11
Open the Terminal and type:

```
gksudo nautilus
```

Now, right click on the folder you want to change the permissions for, select Properties then the Permissions tab. You should now be able to change them.

You could also type:

```
sudo chown [username] [folder]
```

---

### Post by celticbhoy on 2008-09-11
[http://ubuntuforums.org/showthread.php?t=405242](http://ubuntuforums.org/showthread.php?t=405242)

---

