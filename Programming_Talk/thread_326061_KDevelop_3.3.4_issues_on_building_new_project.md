---
title: "KDevelop 3.3.4 issues on building new project"
date: 2006-12-26
forum: Programming Talk
---

### Post by StarsAndBars14 on 2006-12-26
I've been using KDevelop 3.3.4 and trying to make some headway into KDE/Qt programming but I've had some strange errors along the way and want some input on possible fixes for them.

**Issue 1**

When I go to my project "Build" tab and hit "Run automake && friends", I get this message:

> 
This Makefile is only for the CVS repository
This will be deleted before making the distribution
<br />
*** YOU'RE USING autoconf (GNU Autoconf) 2.60.
*** KDE requires autoconf 2.53 or newer
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
*** Exited with status: 2 *


If KDE requires > autoconf 2.53 and I'm using 2.60, shouldn't this be enough for make to continue its process instead of bailing out?  I have WANT_AUTOMAKE_1_6 and WANT_AUTOCONF_2_5 to "1" in my Project Options > Make Options tab.  

**Issue 2**

Building a project and going to the "Build" > "Execute Program" tab results in . . .nothing.

Debug > Start gives me a message like this:  

> 
Could not start program ".
The application does not have the executable bit set. Try rebuilding the project, or change permissions manually.


I've done both, and deleted everything in debug/src, and performed a project clean.  None of that works and I still get the same message.

I'm taking these steps on different projects, and getting the same result.  
Something must be up.  Any ideas?

---

