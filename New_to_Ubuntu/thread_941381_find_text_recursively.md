---
title: "find text recursively"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Guardian2008 on 2008-10-08
I installed Meld after it was recommended to me but there does not seem to be any way to 'find' a specific text string recursively within a directory, the find function only seems to work when I have two open files being 'compared'.

Does anyone know of a suitable software product with GUI that will allow me to search for specific text recursively through a directory structure?

---

### Post by talsemgeest on 2008-10-08
Wouldnt it just be easier to use command line tools?

---

### Post by vanadium on 2008-10-08
The standard "Find" utility should do that: "Places - Search for files". If you click "select more options", you can specify a text string.

---

### Post by porchrat on 2008-10-08
If you are looking to find filenames then use "find" like this:

```
find /directory/path/to/search -name "filename or part thereof"
```

If you need to find text within files recursively through a directory tree use grep:

```
grep -R "string to search for" /path/to/directory
```

Hope this helps.

---

