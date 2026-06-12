---
title: "PyBash"
date: 2009-11-05
forum: Programming Talk
---

### Post by Sandsound on 2009-11-05
Can someone please tell me why this doesn't work :
```
os.system('gksudo "cp -f /home/sandie/Desktop/folder/* /home/sandie/Desktop"')
```

I can do this :
```
os.system("cp -f /home/sandie/Desktop/folder/* /home/sandie/Desktop")
```
but get a "cp: cannot stat" error when I include gksudo ?

---

### Post by NoaHall on 2009-11-05
Why use gksudo for a cli command?

---

### Post by sisco311 on 2009-11-05
```
os.system("gksudo \"bash -c 'cp -f /source/dir/* /dest/dir'\"")
```

in karmic you can use pkexec (policykit): 

```
os.system("pkexec cp -f /source/dir/* /dest/dir")
```

it works much better with cli commands than gksu.

---

### Post by juancarlospaco on 2009-11-05
import os
os.system("gksudo \"xterm -e 'cp -f /source/dir/* /dest/dir'\"")

---

### Post by Sandsound on 2009-11-05
> **NoaHall said:**
> Why use gksudo for a cli command?

It's a Python program with a gui and I don't want the whole program to run as root only the things that require it.

---

### Post by Sandsound on 2009-11-05
> **sisco311 said:**
> ```
os.system("gksudo \"bash -c 'cp -f /source/dir/* /dest/dir'\"")
```

in karmic you can use pkexec (policykit): 

```
os.system("pkexec cp -f /source/dir/* /dest/dir")
```

it works much better with cli commands than gksu.

thanks, but I kind'a like the minimalistic way gksudo ask for authorization.
Does pkexec behave like gksudo ? (if i do a gksudo it remember the authorization and the next gksudo will not prompt for password).

---

### Post by Sandsound on 2009-11-05
> **juancarlospaco said:**
> import os
os.system("gksudo \"xterm -e 'cp -f /source/dir/* /dest/dir'\"")

I did have "import os" but the xterm did the trick.

Thanks :-D

---

