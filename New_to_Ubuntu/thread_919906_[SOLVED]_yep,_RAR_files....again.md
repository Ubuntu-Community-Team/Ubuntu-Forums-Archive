---
title: "[SOLVED] yep, RAR files....again"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by rockerphil on 2008-09-14
ok, i'm sure this questions has been asked before, but i've searched around and still havn't found the answer i'm needing. so, does anyone know of (prefferably) a native Linux program for handling .rar format archives, or at least a Windows app that will work in Wine? any help is greatly appreciated, much thanx,

Phil

---

### Post by perlluver on 2008-09-14
> **rockerphil said:**
> ok, i'm sure this questions has been asked before, but i've searched around and still havn't found the answer i'm needing. so, does anyone know of (prefferably) a native Linux program for handling .rar format archives, or at least a Windows app that will work in Wine? any help is greatly appreciated, much thanx,

Phil

Go to System>Administration>Synaptic and search for unrar.  Or from the terminal, ```
sudo apt-get install unrar
```

---

### Post by OutOfReach on 2008-09-14
I thought that file-roller had RAR support.

---

### Post by Gannon8 on 2008-09-14
p7zip with the p7zip-rar extension can handle rar files.
```
sudo apt-get install p7zip-rar
```(It will automatically install p7zip as a dependency.

---

### Post by aomlives on 2008-09-14
> **OutOfReach said:**
> I thought that file-roller had RAR support.

I'm afraid not, unrar should be fine though.

---

### Post by Yannick Le Saint kyncani on 2008-09-14
> **OutOfReach said:**
> I thought that file-roller had RAR support.

File-roller has rar support through external tools, and you have to install those.

AFAIK, to uncompress rar archives in ubuntu, you can rely on either unrar (which is not free), unrar-free or p7zip-full.

I prefer unrar-free.

---

### Post by rockerphil on 2008-09-14
no, file roller doesn't have rar support, that's the first archive manager i attempted to extract the archive with. now, i've got unrar installed, but it seems to be a command line app, how exactly do i use it? just a quick rundown on how to extract basic rar files would be greatly appreciated

Phil

---

### Post by AndyCooll on 2008-09-14
> **rockerphil said:**
> no, file roller doesn't have rar support, that's the first archive manager i attempted to extract the archive with. now, i've got unrar installed, but it seems to be a command line app, how exactly do i use it? just a quick rundown on how to extract basic rar files would be greatly appreciated

Phil
Once you've installed unrar, go back and use file-roller again. It should now have rar support.

:cool:

---

