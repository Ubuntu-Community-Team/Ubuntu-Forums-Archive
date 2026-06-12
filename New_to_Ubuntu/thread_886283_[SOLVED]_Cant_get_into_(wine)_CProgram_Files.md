---
title: "[SOLVED] Cant get into (wine) C:\Program Files"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2008-08-11
when I try to go into c\Program files it says that there is no such directory.....


```
ncts@ncts:~$ cd .wine
ncts@ncts:~/.wine$ ls
dosdevices  drive_c  system.reg  userdef.reg  user.reg
ncts@ncts:~/.wine$ cd drive_c
ncts@ncts:~/.wine/drive_c$ ls
Program Files  windows
ncts@ncts:~/.wine/drive_c$ cd Program Files
bash: cd: Program: No such file or directory
ncts@ncts:~/.wine/drive_c$ 

```



Why...?

---

### Post by eightmillion on 2008-08-11
Try **cd Program\ Files**
You have to escape the space.

---

### Post by iaculallad on 2008-08-11
Or, enclose it in double quotes:

```
cd "Program Files"
```

EDIT: The reason maybe is to remove ambiguity between the names as they are considered two different names, so you have to place the break (\) character or the (") quote character so the shell would know that it's one item name.

---

### Post by y@w on 2008-08-11
Just start typing Program and hit tab. It'll fill it out for you with the proper escaping (assuming you're using bash or similar shell with tab completion) :)

---

### Post by Ducatiboy Stu on 2008-08-11
Thanks Guys...makes sense now

---

