---
title: "DVD playback error"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by highlyevolved on 2008-07-08
I'm trying to instal libdvdcss2 because currently I can't play dvds but when I try installing it via the terminal I get this error

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

What does this mean?

thanks

---

### Post by nothingspecial on 2008-07-08
You need to add the medibuntu repository to install libdvdcss2.


```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list 
```

then

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Then try installing the package again.

:-\"

---

