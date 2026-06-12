---
title: "[SOLVED] .rar file types?"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by Skyker on 2008-09-26
How can I get my Xubuntu to unpack or at least open .rar file types.  I have all my music zipped/archived into .rar on my memory stick and would like to unpack them.

---

### Post by zvacet on 2008-09-26
```
sudo apt-get install rar unrar p7zip p7zip-full p7zip-rar
```

After that right click on rar file and select **extract here**.

---

### Post by sisco311 on 2008-09-26
Install *unrar* from Synaptic Package Manager, Add/Remove... or
from a terminal:
```
sudo aptitude install unrar
```then right click on the .rar file and select the *Extract Here* or the *Extract To ..* option 

or double click on the files and use the default archive manager to extract the files.

---

### Post by Skyker on 2008-09-26
<3 thanks guys :D  that was easy enough

---

### Post by mike1234 on 2008-09-26
I install "unrar" and "unrar-free" in synaptic. Searching for "unrar" reveals both candidates.

Unarchiver for .rar files (non-free version)
Unrar can extract files from .rar archives. If you want to create .rar
archives, install package rar.

Unarchiver for .rar files
Unrar can extract files from .rar archives. Can't handle some archives in the RAR 3.0 format, only the non-free "unrar" package can do that.

M.

---

