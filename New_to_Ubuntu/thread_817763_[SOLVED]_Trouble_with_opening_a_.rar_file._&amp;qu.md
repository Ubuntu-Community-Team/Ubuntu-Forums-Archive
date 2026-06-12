---
title: "[SOLVED] Trouble with opening a .rar file. &amp;quot;Archive type not supported&amp;quot;?"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by PureRicanGringo on 2008-06-03
I downloaded a torrent of an ebook and I click on the folder and that takes me to a .rar file (the icon is like a little cardboard box) I then right-click and select "extract here" and what comes up is an error message saying "Could not open "Card, Orson Scott.part4.rar" Archive type not supported". The same thing happens if I just double click on the little cardboard box icon instead of attempting to "extract here". I don't get it, I thought .rar files were the favorite archive type. what am I doing wrong? Is this even the right place to post this?

---

### Post by InfinityCircuit on 2008-06-03
```
sudo apt-get install unrar
unrar e FILE_TO_EXTRACT
```

unrar is not free software I believe so that might be why it's not in the default distribution.

---

### Post by iaculallad on 2008-06-03
Or you could try installing [PeaZip]("http://giorgiotani.interfree.it/peazip-unace-plugin_1.LINUX.INSTALL-1.i586.deb"), its free and supports rar archives.

---

### Post by tamoneya on 2008-06-03
you can also use ```
sudo apt-get install rar
```Then the rar files can be handled by the ubuntu archive manager.

---

### Post by PureRicanGringo on 2008-06-04
All who replied were helpful and I am grateful. Thank you very much.

---

