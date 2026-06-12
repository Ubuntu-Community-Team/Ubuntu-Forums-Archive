---
title: "Folder permissions"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by tortelini on 2012-01-04
Hey , i'm a total novice regarding UBUNTU , so here's the problem 

The directory www has permissions :

**drwxrwsr-x  3 root admins 4096 2012-01-04 01:08 www**

And the group admins contains : 

**admins: x:1001:ziga,www-data**

But I cannot create file or folder in directory www , 

any clues ? :D

---

### Post by sanderd17 on 2012-01-04
drwxrwsr-x is in any case not a correct permission. The 's' makes no point.

Can you check again?

---

### Post by tortelini on 2012-01-04
Thanks , found it 2 sec before your post :D , 
sudo chmod g-s www did the trick

---

### Post by sanderd17 on 2012-01-04
you should add an 'x' permission for that group though.

---

