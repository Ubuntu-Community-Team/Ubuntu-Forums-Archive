---
title: "HOWTO: Crossover office 4.2 menus in Hoary"
date: 2005-04-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Darrena on 2005-04-12
Many people have reported problems getting the Crossover office menu's to work in Hoary, others have had no problems at all.  

I was one of the ones having the problem and here is my solution, note I have no idea what these permissions should be set to so changing them could be a bad thing!

It seems that the problem is that CXOffice can't write to $home/.config/menus, so change the permission to give everyone write access before installing.  You can change it back afterwards to 755.

from a terminal:
```
cd $home
sudo chmod 777 .config/menus -R
```

Install CXOffice again.

To change the permissions back type (Or at least mine was this):
```
sudo chmod 755 .config/menus -R
```

---

### Post by Technoviking on 2005-04-13
I had this problem with 4.1, but not with 4.2.

Mike

---

### Post by kuleali on 2005-04-13
thank's, this helped

---

### Post by 23meg on 2005-04-28
this doesn't work for me; i get an "chmod: cannot access `.config/menus': No such file or directory" error when i type sudo chmod 777 .config/menus -R ...

---

### Post by Paulus on 2005-05-11
run it from a normal terminal, though this didn't work for me either :/  the menu's have always seemed a bit dodgey, some changes only take effect after a log out>log in.

---

### Post by flurdy on 2005-06-10
.config is not a my home folder nor does there exist any menus folder or file.

Did you upgrade from a earlier version of Ubuntu?

---

