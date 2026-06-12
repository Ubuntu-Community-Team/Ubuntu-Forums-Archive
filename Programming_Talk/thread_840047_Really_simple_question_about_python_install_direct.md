---
title: "Really simple question about python install directory"
date: 2008-06-25
forum: Programming Talk
---

### Post by brettnak on 2008-06-25
So, I'm just using whatever version of python with my ubuntu install, hardy, and python 2.5.2 and I just got beautifulsoup of the internet and I can't figure out which directory to put it in - it's just one file - so that I don't have to worry about including the file in every directory that I want to use it in.

Thanks
b

---

### Post by elithrar on 2008-06-25
```

/usr/lib/python2.5/site-packages/

```

All libraries/packages you add should go there under a standard Python install with Ubuntu - typically this is referred to as your PYTHONPATH.

After that you can just run an [FONT="Lucida Console"]import package-name[/FONT] from your scripts!

---

### Post by brettnak on 2008-06-25
Thanks, that's exactly what I needed!

---

