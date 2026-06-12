---
title: "cannot delete folder from trash"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Matt26 on 2008-08-11
is there a way that i can delete a folder from my trash when it won't delete normally?  whenever i try to remove the folder i get an error message about not having appropriate permissions to delete the folder- any ideas?  thanks.

---

### Post by Ryadt on 2008-08-11
Try ```
gksudo nautilus
```then go in trash and delete the file.

---

### Post by ukripper on 2008-08-11
> **Matt26 said:**
> is there a way that i can delete a folder from my trash when it won't delete normally?  whenever i try to remove the folder i get an error message about not having appropriate permissions to delete the folder- any ideas?  thanks.

in terminal type:
```
sudo chown -R **yourusername**:**yourusername** ~/.trash/**foldername**
```

replace yourusername and foldername(you want to delete)

and then go to trash and delete

---

### Post by Vivaldi Gloria on 2008-08-11
> **ukripper said:**
> in terminal type:
```
sudo chown -R **yourusername**:**yourusername** ~/.trash/**foldername**
```


Trash is in 

```
/home/<your_username>/.local/share/Trash
```

now.

Matt26, 

Delete the things in the above folder folder. Sometimes a restart fixes things.

If you have more than one disk drive then goto their mount points and also delete the .trash* folders.

Note that the files that start with a dot are hidden and you need to press ctrl+H in nautilus to see them.

---

### Post by issih on 2008-08-11
The above answers are both good ways to get the problem fixed... In the future be careful to use gksudo when running console apps not sudo, its the most common way to end up with this problem :)

Hope that helps

---

### Post by Matt26 on 2008-08-11
thanks for all the suggestions, i will try one of those..

---

