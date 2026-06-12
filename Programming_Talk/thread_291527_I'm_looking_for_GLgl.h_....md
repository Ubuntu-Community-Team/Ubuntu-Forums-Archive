---
title: "I'm looking for GL/gl.h ..."
date: 2006-11-02
forum: Programming Talk
---

### Post by Zalbor on 2006-11-02
I need to use Glut for some programming, and as a result I need the include/GL/gl.h file as well. Why the package that contains it isn't a dependency of freeglut-dev, I don't know, but I can't find that package either. Can anyone tell me which one it is?
I'm currently using Dapper, but I plan to upgrade to Edgy. So if it is a different one in Edgy, please tell me that too. Thank you.

---

### Post by crumja on 2006-11-02
You need to install xorg-devel too.

---

### Post by Zalbor on 2006-11-02
You mean xorg-dev, right? I installed that, the file I need still isn't there...

---

### Post by Zalbor on 2006-11-02
Aha, I found the answer here: [http://ubuntuforums.org/showthread.php?t=235000](http://ubuntuforums.org/showthread.php?t=235000)
(strange, I did make a search for gl.h but it returned no results).

I needed to reinstall mesa-common-dev.

---

### Post by WW on 2007-01-24
I had the same problem reported here and in the thread that Zalbor linked to.  I had mesa-common-dev installed, but the header files were missing.  After reinstalling, the files were installed.  (I am using Ubuntu 6.06.)

---

