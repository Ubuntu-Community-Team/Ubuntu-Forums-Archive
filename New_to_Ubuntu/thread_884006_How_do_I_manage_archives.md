---
title: "How do I manage archives?"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by patrickaupperle on 2008-08-08
I am using kde 4.1 and I can not figure out how to make an archive. I want to create a tar.bz2 then at a later time be able to add files to it. Is this at all possible in kde? I can do it if I go to my gnome side or use file roller, though at next install I will dump gnome all together. So is it possible to at least create a .tar.bz2?

---

### Post by WRDN on 2008-08-08
To create a Gzip archive (with compression), you can use the command:

```
tar czf file.tgz [contents]
```

For a Bzip2 archive with compression:

```
tar cjf file.tar.bz2
```

---

### Post by WRDN on 2008-08-08
[Double Post due to Browser Error]

---

### Post by patrickaupperle on 2008-08-08
> **WRDN said:**
> To create a Gzip archive (with compression), you can use the command:

```
tar czf file.tgz [contents]
```

For a Bzip2 archive with compression:

```
tar cjf file.tar.bz2
```
So, there is no possible way to manage these archives graphically? For the bz2, do I specify contents after that command? Any way to add to an already created archive?

---

### Post by InfinityCircuit on 2008-08-08
In KDE3 you should use the program "ark" to manage archives.  I don't think this has changed in KDE4.

---

### Post by patrickaupperle on 2008-08-08
> **InfinityCircuit said:**
> In KDE3 you should use the program "ark" to manage archives.  I don't think this has changed in KDE4.

Ark exists and extracts quite well. It wont let me create archives or add to them, though. Another incomplete feature? or just me not knowing how to use ark properly?

---

### Post by eightmillion on 2008-08-08
You can use karchiver to create archives on KDE. It's available through adept or from the command line:
> sudo apt-get install karchiver
Ark only extracts as far as I know.

---

### Post by txcrackers on 2008-08-09
I haven't tried ark under 4.1, but under 3.5.9, you **can** create a new archive and drag/drop files/folders from konqueror or dolphin into it, or go through the menu.

---

### Post by patrickaupperle on 2008-08-09
> **txcrackers said:**
> I haven't tried ark under 4.1, but under 3.5.9, you **can** create a new archive and drag/drop files/folders from konqueror or dolphin into it, or go through the menu.

I will test more thoroughly then. When I tried with my tar.bz2, it would not let me at all. Darn, KDE 4.1 is still feature incomplete it seems. :(

---

