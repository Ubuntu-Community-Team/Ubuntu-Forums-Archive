---
title: "Problem working with pdftohtml"
date: 2016-02-02
forum: New to Ubuntu
---

### Post by Balbir_Kumar on 2016-02-02
I compiled and install poppler-0.39.0 as per the instruction. By default header files went int \usr\local\include and lib files went into \usr\local\lib. pdftohtml is installed in \usr\local\bin. Now when I tried to run pdftohtml it gives following error. pdftohtml: error while loading shared libraries: libpoppler.so.58: cannot open shared object file: No such file or directory. Though libpoppler.so.58 is present in \usr\local\lib. Please help me.

---

### Post by steeldriver on 2016-02-02
... as per what instruction? please provide a link if you have one

Is there any reason you can't use the version provided by the poppler-utils repository package?

---

### Post by Balbir_Kumar on 2016-02-03
Hi steeldriver. This issue is resolved now.

---

