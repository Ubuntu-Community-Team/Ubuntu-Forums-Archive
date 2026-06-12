---
title: "[SOLVED] Need an app for RAR files"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by djvasco on 2008-06-23
I'm looking for a good app for extracting and compiling RAR files.  (I've installed 7zip, but am having problems locating and running the program.)  Any suggestions on a good program?

In my previous (Windows) life, I used WinRAR which actually worked out well.  (I'm using the app for my NDS roms.)  WinRAR would extract and automatically compile the files into a .nds format.  Looking for the Ubuntu equivalent.  

I'm running the latest version of Hardy Heron.
Thanks

---

### Post by jualin on 2008-06-23
you can try installing "unrar" from synaptic. And then just use Ubuntu's default Archive Manager to handle the .rar files. Hope this helps!

---

### Post by Biggy on 2008-06-23
install from synaptic  unrar non free

---

### Post by Duck2006 on 2008-06-23
From Synaptic Package Manager,

p7zip
p7zip-full
p7zip-rar

---

### Post by BlueSkyNIS on 2008-06-23
> **jualin said:**
> you can try installing "unrar" from synaptic. And then just use Ubuntu's default Archive Manager to handle the .rar files. Hope this helps!

Into terminal type:

```
sudo apt-get install unrar
```


Cheers

---

### Post by stchman on 2008-06-23
This is the full thing to do for rar and 7z files.

```

sudo apt-get -y install rar unrar p7zip p7zip-full
```

You will be able to create and extract rar and 7zip archives using File Roller.

---

### Post by djvasco on 2008-06-25
Cheers all.  urar worked out.  Also installed p7zip, will test out both to see which one works better.

Mahalo everyone:KS

---

