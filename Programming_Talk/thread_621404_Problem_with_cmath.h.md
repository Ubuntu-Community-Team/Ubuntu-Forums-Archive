---
title: "Problem with cmath.h"
date: 2007-11-23
forum: Programming Talk
---

### Post by Curtisc on 2007-11-23
I'm trying to compile one of the sample applications that comes with ITK.  Strangly, I run into errors in cmath.h:

```
/usr/include/c++/4.1.3/cmath:100: error: ‘::acos’ has not been declared
/usr/include/c++/4.1.3/cmath:117: error: ‘::asin’ has not been declared
/usr/include/c++/4.1.3/cmath:132: error: ‘::atan’ has not been declared
/usr/include/c++/4.1.3/cmath:147: error: ‘::atan2’ has not been declared
/usr/include/c++/4.1.3/cmath:163: error: ‘::ceil’ has not been declared
...

```
This goes on for a while, but you get the point.

If this isn't a C++ problem but an ITK problem, please let me know and I'll go bug the itk users list.  Thanks.

---

### Post by LaRoza on 2007-11-23
Could you post some of the code?

---

### Post by iharrold on 2007-11-23
Yes post the code you are trying to use acos, asin, atan, etc in...

---

### Post by Curtisc on 2007-11-23
I'm not sure which file is calling these functions, but I'm guessing there's something wrong with my compiler configuration rather than the actual source code because it is a demo application included with the library.  The error messages I get only reference header files, not the source code for this particular application.

The first error after all the ::acos not declared etc is an error in [vnl_math.h]("http://www.lems.brown.edu/vision/vxl_doc/html/core/vnl/html/vnl__math_8h-source.html"):147: error: 'lroundf' was not declared in this scope.

I have checked the file vlx_config.h, and the value VXL_C_MATH_HAS_LROUND is defined, so I'm not sure what's going on.

---

### Post by dwhitney67 on 2007-11-24
From the errors above, I'm surprised that you are using GCC 4.1.3.  Can you please confirm that by running this version by executing this command:

```
$ gcc --version
```

---

### Post by samjh on 2007-11-24
> **dwhitney67 said:**
> From the errors above, I'm surprised that you are using GCC 4.1.3.  Can you please confirm that by running this version by executing this command:

```
$ gcc --version
```

He's probably running gcc 4.1.2 with Ubuntu-specific 4.1.3 patches.

If you're running Gutsy, you'll probably have it too.

---

### Post by Curtisc on 2007-11-26
You guys are right, I'm running Gutsy and it's gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2).  Do you think I should roll back to a previous version?

---

### Post by dwhitney67 on 2007-11-26
I would, unless you like testing "pre-release" (or beta release?) software.  I'm surprised that Ubuntu is shipping that version of gcc.  Usually they are not in the business of providing cutting-edge software with their releases.

Fedora 8 was just release in early November (I think Nov 8th), and even it is still using gcc-4.1.2 (to be exact, gcc (GCC) 4.1.2 20070925 (Red Hat 4.1.2-33))

---

### Post by Curtisc on 2007-11-26
Okay, thank you and I will give that a shot.  Do you think I should mention this in a bug report somewhere or anything, or is this an isolated incident?

---

### Post by dwhitney67 on 2007-11-26
Up2U.  But you're catching on... that's why buggy, beta code is released.  So that feedback can be obtained from users.  If you have the time/patience to use a pre-release product, expect to feel frustrated from time to time.

When focusing on a "tree", you tend to lose sight of the "forest".  Have you verified yet whether the original problem you had will be solved by transitioning to gcc-4.1.2?

---

### Post by bruce89 on 2007-11-26
With C you have to add -lm to the GCC command line.

---

### Post by Curtisc on 2007-11-26
After messing around with a bunch of versions of gcc, cmake, etc, I still have no idea what's going on.  I'm going to try a more recent version of the insight-applications, even though my itk build is from the repos and is a couple versions old.  The strange thing is that I can compile and run my own test programs that use itk, I just can't run the sample applications.

---

### Post by Curtisc on 2007-11-26
Okay, thanks all, I feel a little silly for not trying that earlier.  It worked.  I think you were right, it was a problem with the new gcc version.  However, it turned out to work by using the new version of the sample applications, even though I'm using an older version of ITK.  I'm guessing it should have worked with the old version of gcc, but I probably screwed something up.

---

