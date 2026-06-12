---
title: "Why there aren't kernel headers in the repos for this kernel version?"
date: 2014-12-03
forum: Packaging and Compiling Programs
---

### Post by lucas-wolschick on 2014-12-03
I'd like to know why there aren't kernel headers for the newest versions of Linux in the Ubuntu Repos, because that is really an headache when compilling applications that need them, like proprietary drivers and others that mess with the kernel and it's modules. My Linux version is 3.17.0-37. Is there a PPA for this or I will need to continue compilling from the source?

---

### Post by ian-weisser on 2014-12-03
Let's see...
```
$ rmadison -u ubuntu linux
 linux | 2.6.32-21.32  | lucid            | source
 linux | 2.6.32-68.135 | lucid-security   | source
 linux | 2.6.32-68.135 | lucid-updates    | source
 linux | 2.6.32-69.136 | lucid-proposed   | source
 linux | 2.6.32.21.16  | lucid            | ia64, sparc
 linux | 2.6.32.21.22  | lucid            | amd64, i386
 linux | 2.6.32.68.62  | lucid-security   | ia64, sparc
 linux | 2.6.32.68.62  | lucid-updates    | ia64, sparc
 linux | 2.6.32.68.75  | lucid-security   | amd64, i386
 linux | 2.6.32.68.75  | lucid-updates    | amd64, i386
 linux | 2.6.32.69.63  | lucid-proposed   | ia64, sparc
 linux | 2.6.32.69.76  | lucid-proposed   | amd64, i386
 linux | 3.2.0-23.36   | precise          | source
 linux | 3.2.0-72.107  | precise-security | source
 linux | 3.2.0-72.107  | precise-updates  | source
 linux | 3.2.0-73.108  | precise-proposed | source
 linux | 3.2.0.23.25   | precise          | amd64, i386
 linux | 3.2.0.72.86   | precise-security | amd64, i386
 linux | 3.2.0.72.86   | precise-updates  | amd64, i386
 linux | 3.2.0.73.87   | precise-proposed | amd64, i386
 linux | 3.13.0-24.46  | trusty           | source
 linux | 3.13.0-40.69  | trusty-security  | source
 linux | 3.13.0-40.69  | trusty-updates   | source
 linux | 3.13.0-41.70  | trusty-proposed  | source
 linux | 3.16.0-9.14   | ubuntu-rtm/14.09 | source
 linux | 3.16.0-23.31  | utopic           | source
 linux | 3.16.0-25.33  | utopic-security  | source
 linux | 3.16.0-25.33  | utopic-updates   | source
 linux | 3.16.0-25.33  | vivid            | source
 linux | 3.16.0-26.35  | utopic-proposed  | source
```

I don't see a 3.17 kernel in the Ubuntu repositories.
So lacking the headers seems understandable.
 
Perhaps you obtained the 3.17 kernel from a PPA or other source?
Regardless, check out the Ubuntu Kernel Team PPA for future kernels and headers: [http://kernel.ubuntu.com/~kernel-ppa/](http://kernel.ubuntu.com/~kernel-ppa/)

---

