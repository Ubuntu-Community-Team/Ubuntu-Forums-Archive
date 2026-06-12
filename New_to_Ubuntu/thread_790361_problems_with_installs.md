---
title: "problems with installs"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-05-11
I am having problems installing the bin file for google earth and thunderbird.

I have tried doing the sudo thing but have had no luck.

---

### Post by Biggy on 2008-05-11
From Aplications >Accessories >Terminal , type :

> chmod a+x name_of_file.bin
> sudo ./name_of_file.bin

---

### Post by saskatchewan on 2008-05-11
Here is what I typed and the response that I received.

shawn@shawn-laptop:~$ chmod a+x googleearthlinux.bin
chmod: cannot access `googleearthlinux.bin': No such file or directory

yet the file is right on the desktop.

---

### Post by bumanie on 2008-05-11
Can't help with google earth, but thunderbird is in synaptic > sudo apt-get install thunderbird You don't need to go through the hassle of installing a .bin file. From synaptic all dependencies etc. are taken care of and thunderbird will be downloaded and ready to configure.

---

### Post by Monicker on 2008-05-11
But you were not in the Desktop directory when you ran that command.  Do the following first:

```
cd Desktop
```


An apt-cache search also shows a Google Earth package:

googleearth-package - utility to automatically build a Debian package of Google Earth

---

