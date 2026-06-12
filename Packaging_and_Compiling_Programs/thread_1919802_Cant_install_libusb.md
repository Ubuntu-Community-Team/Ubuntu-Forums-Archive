---
title: "Cant install libusb"
date: 2012-02-03
forum: Packaging and Compiling Programs
---

### Post by amtanay on 2012-02-03
I downloaded libusb-1.0.8.tar.bz2 and tried installing it 
1. Extracted
2. sudo ./configure
3. make 
4. make install

but still i cant use the header file in any of my programs.

Please help asap.

---

### Post by MadCow108 on 2012-02-03
from source installs usually go into /usr/local which is not searched by the compiler by default.
you have to add -I/usr/local/include -L/usr/local/lib (or whatever prefix you choose) to the compile lines of other programs.
if they are also configure based they often have a switch named something like --with-libusb=/usr/local, see configure --help of those programs.

---

