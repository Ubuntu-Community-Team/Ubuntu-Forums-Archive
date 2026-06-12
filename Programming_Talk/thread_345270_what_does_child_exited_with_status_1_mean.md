---
title: "what does child exited with status 1 mean"
date: 2007-01-24
forum: Programming Talk
---

### Post by dsimpson on 2007-01-24
I have been having problems with cups and cupsd and when I try to install I get the error message "cupsd child exited with status 1, as well as subprocess post-installation script returned error exit status 2. Does the status 1, and 2, tell you anything about the error or problem that will help with a remedy. I am not Linux competent in any way so I will need anything and everything explained in a simple street level language. Thank you

---

### Post by stoffe on 2007-01-24
It doesn't really tell you anything, no. A Linux process can exit with different numbers, where 0 (zero) means everything went well. 1 is a general "something failed", and 2 is an odd Bash thing I think, that don't really mean much either.

There are some codes that do bear some info, but in general, all you get is "oops".

Instead, when stuff like this happens, try to find the appropriate logs, in this case probably under /var/log/cups/

Hope that helps.

---

### Post by dsimpson on 2007-01-24
Thanks. did just that checked the error_log and found a couple of lines that are causing the problem, now to figure what  code to enter to fix it. At least I know now not to put too much emphasis on the numbering in errors. I was hoping it would point you in the general direction to ease troubleshooting..

---

