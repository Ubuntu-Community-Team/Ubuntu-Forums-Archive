---
title: "Can someone translate this .bat into .sh for me?"
date: 2012-07-31
forum: New to Ubuntu
---

### Post by suvindu on 2012-07-31
```
@echo off
COLOR 04
title BainScape Client v16 is running!
start javaW -splash:.fub_file_store_32/Splash.gif -Xmx500m -cp .;Theme.jar Gui 0 0 highmem members 32
exit
```

File Name: Launch Client.bat

Thanks. :)

---

### Post by juancarlospaco on 2012-07-31
```
java -jar Theme.jar Gui 0 0 highmem members 32
```

---

