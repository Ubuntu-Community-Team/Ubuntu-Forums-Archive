---
title: "error compiling wxwidgets2.6.2"
date: 2006-03-26
forum: Programming Talk
---

### Post by MasterZ on 2006-03-26
Hello, 

I got a problem when compiling wxWdgets2.6.2. 
I have to compile it myself because I need to do it with GTK1.2 for amule 2.1.1 compilation.

I installed with synaptics : 
libgtk1.2-dev
libgtk1.2
libgtk1.2-common
gcc 3.4

Then I do the ./configure on the wxWdgets2.6.2 (I tested it with many options :"--with-gtk=1"  then  "--disable-gtk2 --with-gtk" ).
This part completes ok, but when I do the make I always have this error:

```
../src/generic/statusbr.cpp:325: internal compiler error: Segmentation fault
Please submit a full bug report,
```

I I try again, the error comes on another file, but it's always "Internal compiler error: Segmentation fault" ... 

I tried to compile it with gcc 3.4 et gcc 4.0 ... 

Can someone help me ? 

Thanks,


MasterZ

---

### Post by gord on 2006-03-26
that error is disconcertingly vauge, but just so you know, you can compile amule with gtk2 support (i did)

---

