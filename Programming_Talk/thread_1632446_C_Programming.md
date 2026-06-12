---
title: "C Programming"
date: 2010-11-28
forum: Programming Talk
---

### Post by Arthur.Felty on 2010-11-28
Is Ubuntu a good base OS to use for C compiling, debugging, and development?
And if so where are the best resources found for this?

---

### Post by HermanAB on 2010-11-28
Sure it is.  The whole thing is written in C.

Install the kernel source and compile the kernel.  After that your GCC toolkit will be configured and working and you will have some idea what is going on.

---

### Post by GregBrannon on 2010-11-28
HermanAB's advice might be too much for a beginning programmer.

I suggest you visit the Programming Talk sub forum here on the Ubuntu Forum and review the stickies there that answer your question directly.  There are also many threads in that area that touch on many aspects of the answer to your question.

Yes, all (OK, most, if not all) Linux distributions are excellent OSs in which to set up a programming environment to learn most any programming language.  This is true for all target platforms and OSs but to a lesser degree for the Mac/OS X family.

Good luck!

---

### Post by lisati on 2010-11-28
*Thread moved to **[Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39")**.*

---

### Post by nvteighen on 2010-11-28
Actually, development platforms are set up by tools, not by the OS. Windows can be a good development platform too. The difference, of course, is that Ubuntu (Debian) has repositories from which you can get all the stuff you need for a C and C++ toolchain by doing:

```

sudo apt-get update && sudo apt-get install build-essentials

```

This will 1) update the apt-get database and then install the build-essentials package which installs the C and C++ Standard Library development headers and some other tools like GNU make.

After that you may want to install an IDE or a full-fledged editor like vim or emacs.

---

### Post by v1ad on 2010-11-28
For an IDE i use Geany, even when doing it in Windows i still use Geany.

---

