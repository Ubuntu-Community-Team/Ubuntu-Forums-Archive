---
title: "[CMake] How to use variable name between @@"
date: 2012-02-17
forum: Programming Talk
---

### Post by t1497f35 on 2012-02-17
Hi,
to set the version of the project I define 2 vars ${MinVersion} equal to "ProjectName_VERSION_MINOR" and ${MajVersion} equal to "ProjectName_VERSION_MAJOR".

Then
set(${MinVersion} 0)
set(${MajVersion} 1)

and hook them to "Config.h.in" and "Config.h"
It all works, until next point:
**Problem is, I can't use the var names in the Config.h.in file:**
#define ${MinVersion} @${MinVersion}@
doesn't work, it says I can't use between the two @@ the var names (MinVersion/MajVersion), only their string values (such as ProjectName_VERSION_MINOR).

**Is it possible to use a var name between @@ instead of its value?**

---

