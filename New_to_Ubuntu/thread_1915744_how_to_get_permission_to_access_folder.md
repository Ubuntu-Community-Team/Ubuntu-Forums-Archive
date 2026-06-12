---
title: "how to get permission to access folder"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by rigidigital on 2012-01-26
hi, i am trying to access a folder on a win drive. the folder mounts on startup of virtualbox. its located in media folder and folder name is sf_media. Other times using ubuntu it appears when i need admin privileges ubuntu automatically prompts me for the password. help appreciated. 


[IMG]http://i1095.photobucket.com/albums/i464/Micheal_Lynch/permission.png[/IMG]

---

### Post by sudodus on 2012-01-26
Try to run the file browser Nautilus starting it from a terminal with superuser privileges:
```
gksudo nautilus
```
but be careful, because now you are allowed to delete or move files that are vital for the computer!

*Edit: If you are still unable to display the folder content, you might need to mount the partition in a different way.*

---

