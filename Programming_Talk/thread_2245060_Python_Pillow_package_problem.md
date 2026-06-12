---
title: "Python Pillow package problem"
date: 2014-09-20
forum: Programming Talk
---

### Post by adamitj on 2014-09-20
Hello folks!

After enter a new virtualenv environment, I set to install all Python packages I need:

```
pip install django requests pillow
```

But Pillow does have a problem with image libs support. How can I fix it? The error is below:

```
    --------------------------------------------------------------------
    PIL SETUP SUMMARY
    --------------------------------------------------------------------
    version      Pillow 2.5.3
    platform     linux2 2.7.6 (default, Mar 22 2014, 22:59:56)
                 [GCC 4.8.2]
    --------------------------------------------------------------------
    *** TKINTER support not available
    *** JPEG support not available
    *** OPENJPEG (JPEG2000) support not available
    *** ZLIB (PNG/ZIP) support not available
    *** LIBTIFF support not available
    *** FREETYPE2 support not available
    *** LITTLECMS2 support not available
    *** WEBP support not available
    *** WEBPMUX support not available


```

---

### Post by ian-weisser on 2014-09-21
Well, here's how the python-pil package, in the Ubuntu repositories, solved that problem:

```
$ apt-cache depends python-pil
python-pil
  Depends: python
  Depends: python
  Depends: <python:any>
    python
 |Depends: mime-support
  Depends: python-pil.imagetk
  Depends: libc6
  Depends: libfreetype6
  Depends: libjpeg8
  Depends: liblcms2-2
  Depends: libtiff5
  Depends: libwebp5
  Depends: libwebpmux1
  Depends: zlib1g
  Suggests: python-pil-doc
  Suggests: python-pil-dbg
  Breaks: python-imaging
  Replaces: python-imaging
```

---

### Post by adamitj on 2014-09-23
Yup, thanks for your advice. After that I went deep into a Google research (using these package names) and found a solution that needs to be executed before install pillow inside my virtualenv directory:

```
sudo apt-get install mime-support python-pil.imagetk libc6 libfreetype6 libjpeg8 liblcms2-2 libtiff5 libwebp5 libwebpmux1 zlib1g python-pil-dbg python-dev libjpeg-dev libfreetype6-dev zlib1g-dev
ln -s /usr/lib/`uname -i`-linux-gnu/libfreetype.so /usr/lib/
ln -s /usr/lib/`uname -i`-linux-gnu/libjpeg.so /usr/lib/
ln -s /usr/lib/`uname -i`-linux-gnu/libz.so /usr/lib/
```

And that's all! At least I got JPEG and PNG support that I needed. Thx!


```
    PIL SETUP SUMMARY
    --------------------------------------------------------------------
    version      Pillow 2.5.3
    platform     linux2 2.7.6 (default, Mar 22 2014, 22:59:56)
                 [GCC 4.8.2]
    --------------------------------------------------------------------
    *** TKINTER support not available
    (Tcl/Tk 8.6 libraries needed)
    --- JPEG support available
    *** OPENJPEG (JPEG2000) support not available
    --- ZLIB (PNG/ZIP) support available
    *** LIBTIFF support not available
    --- FREETYPE2 support available
    *** LITTLECMS2 support not available
    *** WEBP support not available
    *** WEBPMUX support not available
```

---

