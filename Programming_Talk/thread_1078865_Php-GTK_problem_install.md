---
title: "Php-GTK problem install"
date: 2009-02-23
forum: Programming Talk
---

### Post by cerealtx on 2009-02-23
yah im trying to install php-gtk so i can make some cross platform stuff, but when trying to compile from source, when trying to do ./buildconf i get ```
cereal@cereal-desktop:~/Desktop/php-gtk-2.0.1$ ./buildconf
/bin/sh: phpize: not found
make: *** [buildmk.stamp] Error 127

```

can't find any information on it, and can't find anything in synaptic or else where

---

### Post by SeanHodges on 2009-02-25
It sounds like your missing the "phpize" program required to compile the code, which is found in the php5-dev package.

To make sure you have ALL the required dependencies, you can run this:

```
sudo apt-get install php5-cli php5-dev php5-gd libgtk2.0-dev libglade2-dev build-essential
```

If the build still doesn't work, you might want to make sure phpize is actually present on your machine, for this try:

```
which phpize
```

The command should return "/usr/bin/phpize".

---

