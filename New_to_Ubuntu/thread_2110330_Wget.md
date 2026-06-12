---
title: "Wget"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by jar26635569 on 2013-01-29
I need help. I'm creating a bash script.

how can i download files using WGET in a website 

i only want to download .gr2 file types without the parent directories.

ex.: http:\\website.com\folder\folder2\folder3\folder4\folder5

the .gr2 files are located in folder5.
i want to download all the .gr2 files inside the subdirectories of folder4  using WGET into one folder.

thanks in advance  :p

---

### Post by von Corax on 2013-01-30
man is your friend. So is Info.

However, you might try
```
wget --recursive --level=2 --no-directories --accept .gr2 http://website.com/folder/folder2/folder3/folder4
```

I haven't tried this; it's just based on my reading of the info pages.

Also, you might get better results if you use "/" instead of "\" as a path separator. :P

---

### Post by jar26635569 on 2013-01-30
thanks, i'll try the code.

---

### Post by HermanAB on 2013-01-30
and don't forget -np or you may get a lot more than you  bargained for.

---

