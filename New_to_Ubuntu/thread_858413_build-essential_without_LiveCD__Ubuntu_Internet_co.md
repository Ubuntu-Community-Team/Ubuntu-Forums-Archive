---
title: "build-essential without LiveCD / Ubuntu Internet connection?"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Jaded Misanthrope on 2008-07-13
Would it be possible for me to install the build-essential package without the use of a LiveCD or a working Ubuntu Internet connection (I do, however, have an Internet connection with Vista, which is dual-booting with Ubuntu, so any files I need can be downloaded and accessed by Ubuntu / moved to my home directory).

The only reason I need this is because Ubuntu insists that I have not inserted the LiveCD when I try to install the package through either the terminal or Synaptic (oddly enough, the disc will mount and prompt me to open Synaptic because it contains packages), and I need to have build-essential to get my wireless Internet connection working (I'm on a laptop and a 'direct' (i.e. wired) connection to the router is not possible).

---

### Post by pytheas22 on 2008-07-13
build-essential installs the packages libc6-dev, gcc, g++, make and dpkg-dev.  You can go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and search for each of those five packages, download the .deb's and transfer them to your Ubuntu partition.  From there you can install them.  You may need to install them in a certain order, so if you get an error message about some dependency not being satisfied, find that dependency and install it first.

---

### Post by Jaded Misanthrope on 2008-07-13
This probably sounds daft, but how would I install them after transferring them over to Ubuntu?

---

### Post by CautionaryX on 2008-07-13
You should be able to double click on them and then they should open.

---

### Post by Jaded Misanthrope on 2008-07-13
Okay, thanks.

---

### Post by Jaded Misanthrope on 2008-07-13
Well, I have encountered a problem--two of the packages I need seem to be dependent on eachother and neither will install unless the other is. They are, if I remember correctly, g++-4.2 and libstdc++6-4.2. How would I bypass this?

---

### Post by Bachstelze on 2008-07-13
Try installing both at the same time. Put both packages in a same directory, open a terminal, browse to that directory and do

```
sudo dpkg -i *.deb
```

---

