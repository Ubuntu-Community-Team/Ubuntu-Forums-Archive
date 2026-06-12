---
title: "[SOLVED] Removing a directory?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by Felixworks on 2008-08-03
I tried to manually install Kompozer but something must've gone wrong so I tried to delete it.  I tried ```
sudo rm kompozer
``` from the directory it was in, but terminal gave me back "rm: cannot remove 'kompozer': Is a directory.  I thought it might've been because there was still stuff inside the directory.  So I went inside kompozer and moved all the files to the trash.  I went back and tried the same code and it gave me the same output.  What's the deal?  You can't delete directories in ubuntu?

---

### Post by ConMan318 on 2008-08-03
You can use
```

rmdir directoryName

```

only if a directory is empty.  If it's not empty, you have to do
```

rm directoryName -rf

```

to recursively force removal.

---

### Post by perlluver on 2008-08-03
wouldn't that be ```
rm -rf /kompozer
```?

---

### Post by Felixworks on 2008-08-03
Oh goodies it worked!  Hehe, thanks for that.  I didn't realize directories were treated differently than files.

---

### Post by perlluver on 2008-08-03
> **Felixworks said:**
> Oh goodies it worked!  Hehe, thanks for that.  I didn't realize directories were treated differently than files.

Please mark as solved in Thread Tools.

---

### Post by Felixworks on 2008-08-03
Yep, I've already got that covered.  Thanks.  And the first one worked for me so...I guess it can go either way.

---

### Post by sayakb on 2008-08-03
```
rm directoryname -rf
```
Should work (as indicated above)

@perlluver:
No, since /foldername would be in / and not inside the directory you want to remove it from.

---

### Post by perlluver on 2008-08-03
> **LinuxIsInnovation said:**
> ```
rm directoryname -rf
```
Should work (as indicated above)

@perlluver:
No, since /foldername would be in / and not inside the directory you want to remove it from.

Oh, that is good to know, thanks.

---

### Post by sayakb on 2008-08-03
@Felixworks
Please mark the thread as solved.

---

