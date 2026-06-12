---
title: "ZIP64 extensions for Python/Numpy"
date: 2009-02-02
forum: Programming Talk
---

### Post by phillies on 2009-02-02
Hi,

I have a problem with Python/Numpy. I need to save lage amounts of data as numpoy zip file with numpy.savez(...). This works fine unless the amount is larger than 4 GB, then I get the exception ```
LargeZipFile: Zipfile size would require ZIP64 extensions
```risen by the zipfile module of python.

My problem is that I did not find usable information about how to enable those extensions. I couldn't even figure out reliably if I have to change something within python or pkzip or somewhere else in ubuntu 8.10.

Some ideas?

Phil

---

### Post by Zugzwang on 2009-02-02
Use your favourite search machine. The solution is in here:

[http://mail.python.org/pipermail/python-bugs-list/2006-July/034192.html](http://mail.python.org/pipermail/python-bugs-list/2006-July/034192.html)

Second post.

---

### Post by phillies on 2009-02-02
Thx for the reply, I did find a lot of python mailing list entries when googleing different combinations of zip, python, zip64, and numpy, but this particular one did not show up. 

Unfortunately, the suggested solution "add allowZip64=True to the zipfile command" is not usable for me as I call numpy's savez() function which does not pass arguments along to zipfile. So I have to file a bug at numpy and meanwhile hack numpy manually.

---

### Post by sjvdwalt on 2009-02-22
Thanks for the bug report.  A patch is available at

[http://scipy.org/scipy/numpy/ticket/991]("http://scipy.org/scipy/numpy/ticket/991")

waiting for review.

---

