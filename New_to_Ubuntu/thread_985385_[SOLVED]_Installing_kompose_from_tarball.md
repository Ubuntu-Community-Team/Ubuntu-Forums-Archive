---
title: "[SOLVED] Installing kompose from tarball"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by annamoo on 2008-11-17
Hi

I am trying to install kompose.  it is a tarball file.
I have uncompressed it to just a folder and tried ```
./configure
```

However i have been getting the error message > checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

I would look in the log but i don't actually know how to do it.

Any ideas????

---

### Post by shifty_powers on 2008-11-17
do you have the build-essential package installed?

```
sudo apt-get install build-essential
```

---

### Post by shifty_powers on 2008-11-17
hang on why from tarball?

it is in the repo's...

```
sudo apt-get install kompose
```

---

### Post by annamoo on 2008-11-18
Hm, I'm not sure!!  Have installed it using apt-get, thanks a lot for your help.

---

