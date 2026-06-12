---
title: "[SOLVED] Thread on Permissions ?"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Drakkor on 2008-08-26
Yeah, I was  looking for a way to grant user permissions for a directory,and all the folders and subfolders inside and the files themselves  :confused:

---

### Post by Oldsoldier2003 on 2008-08-26
you could always chown -R the directory. See ```
man chown
``` for more details. Just be careful because changing ownership of files can sometimes have unintended side effects.

---

### Post by forger on 2008-08-26
You can do it using linux commands, such as chown and chmod

Change the owner:
```
sudo chown -R yourusername /path/to/folder
```

Change the owner and the default group:
```
sudo chown -R yourusername:yourgroup /path/to/folder
```

Change permissions:
```
sudo chmod -R 644 /path/to/folder
```
For permissions and chmod, read this:
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)
[http://www.unixcities.com/howto/index3.html](http://www.unixcities.com/howto/index3.html)
[http://www.google.com/search?q=chmod%20tutorial](http://www.google.com/search?q=chmod%20tutorial)

---

### Post by Drakkor on 2008-08-26
Thanks,guys sudo chown -R yourusername /path/to/folder did it ! :)

---

