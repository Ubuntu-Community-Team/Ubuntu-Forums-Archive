---
title: "Winrar"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by nougat03 on 2008-09-01
I downloaded Winrar and I'm not sure how I can go about opening the program.

I don't know if Winrar can work on Ubuntu or not, if not, what alternatives do I have to Winrar?

---

### Post by pmlxuser on 2008-09-01
if you install wine
```

$sudo apt-get install wine

```

you would install winrar

```

wine /directory/winrar.exe

```

after that you could open it unsing a link on the desktop

---

### Post by sayakb on 2008-09-01
Why do you need Winrar for. At a terminal, do:
```
sudo apt-get install rar unrar
```
And you should be able to open/create rar archives.

---

### Post by Nepherte on 2008-09-01
You can install it by typing:
```
sudo apt-get install unrar
```

---

### Post by ajorpheus on 2008-09-29
xarchiver is a good gui alternative for WinRar

Try this:
sudo apt-get install rar unrar xarchiver

---

### Post by Tom--d on 2008-09-29
> **ajorpheus said:**
> xarchiver is a good gui alternative for WinRar

Try this:
sudo apt-get install rar unrar xarchiver

Rar and unrar are used by the GNOME archive manager. So when you right click the .rar and extract here. It will extract. Same with making archives.

---

