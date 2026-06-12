---
title: "Deleting protected files"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by daz4126 on 2008-04-29
Hi,

I've ended up with a protected file in my trash bin. Now I can't empty the trash, if I try to move it back to my desktop, it says I can't because I don't have permissions. I'm sure it's easy, but does anybody know how I can get rid of this file?

thanks,

DAZ

---

### Post by scragar on 2008-04-29
```
sudo rm ~/.local/share/Trash/files/*
```

---

### Post by meindian523 on 2008-04-29
Go root!

Press Alt+F2,type ```
gksudo nautilus
```,then navigate to YOUR trash folder(would be .Trash-<username> in your home directory,unless you are using 8.04,where they have changed it to ~/usr/.local/share/Trash-<username>),then restore it to wherever you want it.Or delete it,as you wish.

---

### Post by daz4126 on 2008-04-29
Thanks guys - very helpful to know how to get nautilus as root. The other problem was that I couldn't find the trash can in the file system before - why do they keep moving things?!?

DAZ

---

