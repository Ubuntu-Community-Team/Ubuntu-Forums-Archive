---
title: "mod_python form upload: permission denied sometimes..."
date: 2009-04-24
forum: Programming Talk
---

### Post by pzs on 2009-04-24
I have a mod_python application that takes a POST file upload from a form. It works fine from my machine, other machines in my office and my home machine. It does not work from my bosses machine in a different city - he gets "You don't have permission to access this on this server". 

In the logs, it's returned 403. I also have this error in error.log:

Cannot traverse upload in /pythonapps/wiggle/form/upload because <function form at 0x7fe7568e31b8> is not a traversable object, referer: ...

Could this be a network level problem? If so, why does it work from my home machine but not my bosses machine?? The file to upload is quite large - 7MB.

---

