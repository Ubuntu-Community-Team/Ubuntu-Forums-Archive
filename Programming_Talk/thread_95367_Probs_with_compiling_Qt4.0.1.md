---
title: "Probs with compiling Qt4.0.1"
date: 2005-11-26
forum: Programming Talk
---

### Post by meissner on 2005-11-26
I destroy my Hoary while upgrade to Breezy :/ Than I install Breezy completly new. Under Hoary there where no Problem to install Qt4.0.0 and Qt4.0.1. I only need to install some Packages with apt. But now I try to compile Qt4 under Breezy, result:

```
/home/meissner/downloads/qt-x11-opensource-src-4.0.1/lib/libQtGui.so: undefined reference to `deflate'
/home/meissner/downloads/qt-x11-opensource-src-4.0.1/lib/libQtGui.so: undefined reference to `inflate'
/home/meissner/downloads/qt-x11-opensource-src-4.0.1/lib/libQtGui.so: undefined reference to `inflateInit_'
/home/meissner/downloads/qt-x11-opensource-src-4.0.1/lib/libQtGui.so: undefined reference to `crc32'
/home/meissner/downloads/qt-x11-opensource-src-4.0.1/lib/libQtGui.so: undefined reference to `deflateInit2_'
/home/meissner/downloads/qt-x11-opensource-src-4.0.1/lib/libQtGui.so: undefined reference to `inflateReset'
/home/meissner/downloads/qt-x11-opensource-src-4.0.1/lib/libQtGui.so: undefined reference to `deflateReset'
/home/meissner/downloads/qt-x11-opensource-src-4.0.1/lib/libQtGui.so: undefined reference to `inflateEnd'
/home/meissner/downloads/qt-x11-opensource-src-4.0.1/lib/libQtGui.so: undefined reference to `deflateEnd'
```

With google and IRC I find out, that I probably need the libz Packages. But I don't get a Source for this one.

So I need help, thanks

---

### Post by gord on 2005-11-26
are you sure you don't meen zlib? 
```
 sudo apt-get zlib1g zlib1g-dev 
```

---

### Post by meissner on 2005-11-27
I install these package befor I post here, but I must perform a make confclean and configure. That was my mistake. Now it works. Nice.

---

