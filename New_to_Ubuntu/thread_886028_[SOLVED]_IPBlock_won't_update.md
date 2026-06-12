---
title: "[SOLVED] IPBlock won't update"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by rbjscv on 2008-08-10
My apologies if this is here twice.

August 10th, IPBlock won't update.  I tried uninstalling it, and still same thing.  I get 0 ranges.

Anything I need to look at?  Does this just happen from time to time?

---

### Post by SZ07 on 2008-08-10
This is a stupid question but since you reinstalled it, did you check to see if any lists are added in the list tab?

Also, disable ipblock, then quit it and in the terminal do:
```
sudo ipblock -s
```

then do:

```
 sudo ipblock -l
```

Post what you get.

---

### Post by uljanow on 2008-08-10
[http://ubuntuforums.org/showpost.php?p=5563010&postcount=247](http://ubuntuforums.org/showpost.php?p=5563010&postcount=247)

---

### Post by rbjscv on 2008-08-10
It started back up. Must have been on their end. Everything updated and is running fine again.

Merci beaucoup

---

