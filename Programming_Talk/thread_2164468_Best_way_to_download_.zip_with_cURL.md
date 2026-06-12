---
title: "Best way to download .zip with cURL?"
date: 2013-07-31
forum: Programming Talk
---

### Post by ?#Yhf%*&amp; on 2013-07-31
Hello all!
I'm writing a bash script that creates Minecraft modpacks. One of the steps is to download a mod loader, in the format of an online zip file. I plan to use this on systems that don't have wget installed (and can't be installed), so what's the best way to download a zip file using cURL? I've tried:

```
curl http://www.example.com/path/to/file.zip > "path/to/modpack.zip"
```

Thanks in advance!

---

### Post by Vaphell on 2013-08-02
*curl --help* says that it supports **-o <output file>** option

---

