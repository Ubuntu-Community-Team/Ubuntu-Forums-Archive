---
title: "Xampp Problem"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by abou maryam on 2008-10-29
hi

i've just installed the xampp on my laptop , i can browse the localhost normaly and acess the phpmyadmin and other application

but the problem it that i have to put my php files on the htdocs , and i can't put any file in this location coz i don't have a privilege to do this action, only the root can acess this folder and put file in it .


so my Question is , how can put my php file in the htdocs location ?

---

### Post by Sarmacid on 2008-10-29
Use sudo to copy or move the files
```
sudo cp file.php /path/to/htdocs/
```

---

### Post by abou maryam on 2008-10-30
thanks for the help

it work's good

but is there any quicly method

can i change the permission of the htdocs and give my user a permission to write files ?

---

### Post by Sarmacid on 2008-10-31
Yes, you can change permissions with the chmod command.```
man chmod
```For more info

---

