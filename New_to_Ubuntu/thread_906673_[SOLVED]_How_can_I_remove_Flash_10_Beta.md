---
title: "[SOLVED] How can I remove Flash 10 Beta?"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by kansasnoob on 2008-08-31
Some time ago I installed flash 10 beta using the tar.gz from Adobe. I now see that flash 10 RC is out so I'd like to give it a whirl, but I'm thinking I should remove the flash 10 beta first and I'm clueless as to how:confused:

---

### Post by coolbrook on 2008-08-31
Close your web browser and then delete libflashplayer.so from home/yourusername/.mozilla/plugins (a hidden folder)

Then you can install the update.

---

### Post by Locke_99GS on 2008-08-31
Delete libflashplayer.so binary and flashplayer.xpt file in directory /home/username/.mozilla/plugins/

---

### Post by kansasnoob on 2008-08-31
I'm probably just being slow here but:

> lance@lance-desktop:~$ home/lance/.mozilla/plugins/
bash: home/lance/.mozilla/plugins/: No such file or directory


---

### Post by benerivo on 2008-08-31
It may have installed the .so file elsewhere such as /usr/lib/mozilla or maybe /usr/lib/firefox or some others. If you search /usr/lib/ for
flash
then you should find any instance where it has been installed.

---

### Post by kansasnoob on 2008-08-31
Got it, I had to:

```
 cd ~/.mozilla
 rm flashplayer.xpt libflashplayer.so
```

Thanks everyone!

---

