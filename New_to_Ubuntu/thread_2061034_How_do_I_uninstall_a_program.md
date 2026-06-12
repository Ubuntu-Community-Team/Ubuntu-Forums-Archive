---
title: "How do I uninstall a program?"
date: 2012-09-21
forum: New to Ubuntu
---

### Post by ZombiesAteMyNeighbors on 2012-09-21
Hello. I downloaded a music player called DeaDBeeF, and after trying out RhythemBox a little more, I've decided I actually like it.

I want to uninstall DeaDBeeF, but when I search for it in the software center, it's not there. I don't see an uninstall thing anywhere, so I was wondering if anyone knew how to uninstall it?

Thanks a lot.

---

### Post by diesch on 2012-09-21
How did you install it?

---

### Post by ZombiesAteMyNeighbors on 2012-09-21
> **diesch said:**
> How did you install it?

From [http://deadbeef.sourceforge.net/download.html](http://deadbeef.sourceforge.net/download.html)

I downloaded the amd64 version if it matters.

---

### Post by diesch on 2012-09-21
The "static portable build"? Then just remove the folder into which you unpacked the archive.

---

### Post by QIII on 2012-09-21
If you added a PPA and then did```
sudo apt-get install packagename
```

you can do```
sudo apt-get purge packagename
```

If you added the PPA and then used a GUI package manager, you can uninstall from there.

diesch's method has an alternative:  if an uninstall.sh is included in the directory, you may also use that.

---

### Post by ZombiesAteMyNeighbors on 2012-09-21
Err, I'm a little confused. I didn't install the portable version.

Basically, I downloaded the amd64 version, which took me to sourceforge, and game me a file which opened in the software center.

I tried to open it again, but in the software center, there's only a reinstall option, not a remove. It doesn't show up if I search for it, and it's not in any of the categories for installed software.

---

### Post by QIII on 2012-09-21
Then try```
sudo apt-get purge packagename
```

Replace "packagename" with the actual package name.

---

### Post by ZombiesAteMyNeighbors on 2012-09-21
> **QIII said:**
> Then try```
sudo apt-get purge packagename
```

Replace "packagename" with the actual package name.

Worked perfectly, thanks!

---

