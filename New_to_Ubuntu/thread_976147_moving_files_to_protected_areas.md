---
title: "moving files to protected areas?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by cloudpersona on 2008-11-09
I've been trying to move some files into a game folder, but when I try it tells me I don't have permission to do that; how do I get permission?

---

### Post by epitaph on 2008-11-09
There are a few ways.

You could run nautilus as root so you have the permissions:

```
sudo nautilus
```

Or, you can open a terminal and use the mv command as root (type sudo in first, then use the mv command).

---

### Post by cloudpersona on 2008-11-09
Thanks much. XD

---

### Post by Nepherte on 2008-11-09
For graphical applications it's advised to use graphical sudo:
```
**gksudo** nautilus
```

---

### Post by fooman on 2008-11-09
even better...install nautilus-gksu and you can right-click anywhere in nautilus and have the option to "open as administrator"...very handy (but use caution when playing as admin) !!

```
sudo apt-get install nautilus-gksu
```

here is another handy one..."nautilus-open-terminal".  it will allow you to open a terminal just about anywhere with a right-click:

```
sudo apt-get install nautilus-open-terminal
```

those are two things i think should be installed by default.

---

