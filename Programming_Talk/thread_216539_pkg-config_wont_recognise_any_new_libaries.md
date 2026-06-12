---
title: "pkg-config wont recognise any new libaries"
date: 2006-07-15
forum: Programming Talk
---

### Post by sharperguy on 2006-07-15
I've been trying to write programs in c++ for a while now, but I cant get any of them to compile because it wont recognise that the libary's I am using are there.

I have narrowed it dont (i think) that pkg-config is not being told about the new libaries when I install them with apt.

Can anyone help?

---

### Post by sharperguy on 2006-07-15
ok, someone else was having this problem (soz 4 double post), but anyway, someone *else* said you needed the "-dev" packages installed, however, i do have those installed.

---

### Post by sharperguy on 2006-07-15
ok, so pkg-config tells me this:

```
$ pkg-config gnet2.0 --cflags --libs
Package gnet2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gnet2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gnet2.0' found

``` 
So I look for gnet2.0.pc and it's in /usr/lib/pkgconfig

So i do:
```
export PKG_CONFIG_PATH=/usr/lib/pkgconfig
``` 
And still the same reults

and if I echo PKG_CONFIG_PATH it does give me /usr/lib/pkgconfig, so now i am really confused :s

---

### Post by sharperguy on 2006-07-15
oh well, this was a helpfull topic it deserves to be jailed. Reason:

i missed out a "-" in the library name

*sigh*

---

