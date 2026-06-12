---
title: "search"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by windowsfree on 2014-05-04
i cannot find anything when i use search, see attached screenshot.  as you can see i installed tweak from the command line, but cannot find it.

any ideas?

---

### Post by steeldriver on 2014-05-04
The database probably didn't get updated yet - try updating it manually

```
sudo updatedb
```

---

### Post by windowsfree on 2014-05-04
tried that, but it didn't work

---

### Post by monkeybrain20122 on 2014-05-04
See if this fixes your problem. Open the file browser, press ctrl+h or choose show hidden files in the menu, delete the folder .local/share/zitgeist and then reboot.

---

### Post by windowsfree on 2014-05-04
i rebooted and everything is back, thanks for all the replies

---

