---
title: "wget where does it save files"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by jonathan21 on 2008-09-22
wget where does it save files

---

### Post by ThrobbingBrain66 on 2008-09-22
It saves to your current directory, unless otherwise specified.

---

### Post by sharks on 2008-09-22
it usually saves in home folder.

---

### Post by aeiah on 2008-09-22
current directory, as has been stated. when you first open a terminal, your current directory will always be your home folder. if you wanted to save to your desktop you'd change directory to the desktop before using wget
```

cd Desktop
wget http://domain.com/path/to/file.ext

```

another handy wget tidbit: use the -c flag to continue a partial download if you have to stop it earlier on

```

wget -c http://domain.com/path/to/file.ext

```

---

### Post by Rayaz on 2008-09-22
An alternate download manager, Downloader for X, which I use for large downlaods. You can download it using Add/Remove Programs from the main menu. Hope you find it useful.

---

