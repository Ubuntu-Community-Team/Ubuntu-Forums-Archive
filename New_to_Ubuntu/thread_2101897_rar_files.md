---
title: "rar files"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by dlw on 2013-01-05
How are *.rar.a files opened.
Archive manager says file not supported.

TIA
dlw

---

### Post by audiomick on 2013-01-05
I think you need a thing called unrar.

[http://home.gna.org/unrar/]("http://home.gna.org/unrar/")

I think it is installed by default.

Look at 
```
man unrar
```

for some info on it.

---

### Post by pqwoerituytrueiwoq on 2013-01-05
either of these commands will add support for rar files
```
sudo apt-get install rar
sudo apt-get install unrar
```

---

### Post by HereInOz on 2013-01-05
You wrote *.rar.a in your original posting.  Is this a mistake, or do you really have a filename ending in .rar.a?

The .a could cause rar to not recognise the file perhaps.  If this is the case, try renaming the file without the .a and see what happens.

---

