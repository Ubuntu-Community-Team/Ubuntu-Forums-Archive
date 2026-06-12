---
title: "Prepare FAKE files on disk   [Python]"
date: 2010-01-02
forum: Programming Talk
---

### Post by baskar007 on 2010-01-02
Any one know how to create files with fake size on disk using python or whatever?
for example, in windows some downloader applications will create fake size files before they download full file.  

if you not undestand:
   when i download a 300mb movie file, the downloader application will create a 300mb size file on my HDD before it download fully.



sorry for my bad english, if you don't understand please tell me.

---

### Post by ssam on 2010-01-02
you can seek to where you want the file to end and write something.
```

f = open("foo", "w")
f.seek(300*1024*1024)
f.write("\0")
f.seek(0)
...
f.close()

```

---

### Post by baskar007 on 2010-01-02
> **ssam said:**
> you can seek to where you want the file to end and write something.
```

f = open("foo", "w")
f.seek(300*1024*1024)
f.write("\0")
f.seek(0)
...
f.close()

```
It's awesome, thankyou.
But i have small doupt, we writing some data at the end of the file ("\0") this may corrupt our file data?

---

### Post by OgreProgrammer on 2010-01-03
> **baskar007 said:**
> It's awesome, thankyou.
But i have small doupt, we writing some data at the end of the file ("\0") this may corrupt our file data?

Just make it a few bytes shorter than the real file if you are concerned about that.

---

### Post by Can+~ on 2010-01-03
> **baskar007 said:**
> It's awesome, thankyou.
But i have small doupt, we writing some data at the end of the file ("\0") this may corrupt our file data?

If you make the fake file of the exact same size as the original one, then it would, sooner or later, be stepped over by the real file, so I would say that you're safe.

---

