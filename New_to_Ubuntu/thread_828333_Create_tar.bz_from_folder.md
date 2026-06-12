---
title: "Create tar.bz from folder"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by MattTait on 2008-06-13
Hi, how can I make a tar.bz from some folder (e.g. /usr/folder)?

---

### Post by nkri on 2008-06-13
Right-click on the folder, and click "Create Archive"
It'll ask you where you want to save it and with what type of compression; one of the types is tar.bz.

---

### Post by sparrowkc on 2008-06-13
You can also use tar from the command line.

---

### Post by drs305 on 2008-06-13
Or, from terminal:
```
sudo tar -cf newname.tar /path/foldername/
sudo bzip2 newname.tar
```

You could combine the two by joining them with "&&"

---

