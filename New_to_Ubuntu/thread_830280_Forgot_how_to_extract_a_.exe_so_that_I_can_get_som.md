---
title: "Forgot how to extract a .exe so that I can get some files contained within..."
date: 2008-06-15
forum: New to Ubuntu
---

### Post by whoscheesemine on 2008-06-15
Using Xubuntu 8.04...

I have completelty forgotten what program to use to extract a .exe file in Xubuntu to get the files contained within. The reason I need this done is so I can get a .sys and a .inf file to use with ndiswrapper or w/e its called, so that I may be able to get my brother's wireless card to work.

---

### Post by sdennie on 2008-06-15
I think you are looking for cabextract:

```

sudo apt-get install cabextract

```

To figure out how to use it type:

```

man cabextract

```

---

### Post by chili555 on 2008-06-15
You might also need *unshield, unzip* and *unrar.* If cabextract doesn't do it, try each of the others.

---

### Post by aktiwers on 2008-06-15
In Gnome I can just right-click and "extract".

---

### Post by whoscheesemine on 2008-06-15
> **aktiwers said:**
> In Gnome I can just right-click and "extract".

Yeah, I can do that in Gnome too, does anyone know the package that lets you do that in gnome, so that i may do it in xfce?

Oh, btw cabextract worked, thanks.

I'd say solved, but I still don't know what package to download so that I can have that one option in XFCE too.

---

### Post by aliencam on 2008-10-17
sorry to revive a dead topic, but if anyone needs to do this to a larger file, like a program, 7z will do it.  just type (in terminal): 
```
7z x ~/filename.ext
```

---

