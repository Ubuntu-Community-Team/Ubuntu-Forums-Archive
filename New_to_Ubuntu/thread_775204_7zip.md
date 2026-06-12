---
title: "7zip"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-04-29
How do you get 7zip to zip a file?

---

### Post by Monicker on 2008-04-29
> **saskatchewan said:**
> How do you get 7zip to zip a file?

```
7z a -tzip foo.zip foo.txt
7z a -tzip foo.zip *.txt
```

---

### Post by saskatchewan on 2008-04-29
Is there a way to do it without commands?

---

### Post by lwvmobile on 2008-04-29
You can just right click on the desired target(s) and click create archive.

You may have to do a 

```
sudo apt-get install p7zip-full
```

first to install support for 7zip though.

---

### Post by saskatchewan on 2008-04-30
That did the trick

Thanks

---

