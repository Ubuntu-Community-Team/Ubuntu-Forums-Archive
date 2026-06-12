---
title: "Compiling OpenCV in Eclipse"
date: 2012-03-30
forum: Programming Talk
---

### Post by boblettoj99 on 2012-03-30
Hello, 

I want to incorporate some OpenCV into my existing c++ project.

I have linked to the opencv lib files. "Library search path" in eclipse linker is "usr/local/lib", and "Libraries" are "cv" and "highgui".

I think I already have opencv2.3.1 installed, but the latest error I'm getting is "cannot find -lcv.so" (the same for highgui).

The includes seem to be working though.. Can anyone help me remove this error?

---

### Post by boblettoj99 on 2012-03-30
It seems you need to include the version stuff in the libraries.

fixed it with opencv_cv231 instead of cv, opencv_highgui231 for highgui etc.

:p

---

