---
title: "problem installing .py software (Sublime Text)"
date: 2015-09-13
forum: New to Ubuntu
---

### Post by Yarinka on 2015-09-13
Hi all,

I just installed Ubuntu for the very first time and having troubles installing Sublime Text - it's not available trough Software Centre, so I downloaded the package for Linux that was offered to me on their main page. 
```
drwxr-xr-x 7 irina irina    4096 Jul  8  2013 Icon
drwxr-xr-x 2 irina irina    4096 Jul  8  2013 lib
-rw-r--r-- 1 irina irina    4206 Jul  8  2013 PackageSetup.py
-rw-r--r-- 1 irina irina    4709 Sep 15 00:22 PackageSetup.pyc
drwxr-xr-x 2 irina irina    4096 Jul  8  2013 Pristine Packages
-rw-r--r-- 1 irina irina   10838 Jul  8  2013 sublime_plugin.py
-rw-r--r-- 1 irina irina   13435 Sep 15 00:22 sublime_plugin.pyc
-rwxr-xr-x 1 irina irina 8662712 Jul  8  2013 sublime_text
```
that's are the files in the package. I tried ```
$ python PackageSetup.py
``` but nothing happens...

I would greatly appreciate any help with this,

Irina

---

### Post by cariboo on 2015-09-13
Go to the directory Sublime text is located in and type:

```
./sublime_text
```

The app should start up.

---

### Post by mystics on 2015-09-14
Here's one way to install it: [http://askubuntu.com/questions/172698/how-do-i-install-sublime-text-2-3](http://askubuntu.com/questions/172698/how-do-i-install-sublime-text-2-3)

You could also get the DEB file and install it that way. Sublime Text has information on this on unofficial documentation: [http://sublime-text-unofficial-documentation.readthedocs.org/en/latest/getting_started/install.html](http://sublime-text-unofficial-documentation.readthedocs.org/en/latest/getting_started/install.html)

---

