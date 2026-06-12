---
title: "how do i find the kernal version of my distro"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by determinedblkman on 2008-08-30
how do i find the kernal ver. for my distro? it seems i have find the "kernal header package" for my kernal. but i have to know my kernal ver.

---

### Post by OutOfReach on 2008-08-30
Goto System>Administration>System Monitor and to the System tab, it should say the kernel. 
Or you can goto the terminal and type in:
```
uname -r
```

---

### Post by drs305 on 2008-08-30
```
uname -r
```

is what you are looking for.

```
/home: uname -r
2.6.24-19-generic

```

---

### Post by rggavubt on 2008-08-30
If you don't like terminal commands, you can install "sys info".  Search for it on Applications, Add/Remove.  Also lists other system information.

---

### Post by kansasnoob on 2008-08-30
Or just go to System > Administration > System Monitor which is installed by default:

[ATTACH]83431[/ATTACH]

---

