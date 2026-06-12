---
title: "Jdeveloper problems :("
date: 2006-03-09
forum: Programming Talk
---

### Post by sparty on 2006-03-09
Hello all,

I'm currently trying to set up a development environment, on ubuntu 5.10 to code against the oracle collaboration suite on a remote server. I've downloaded the relevant sdks and libs to the required machine, however when running a project it is not finding the required files because they are not visible in the path ?

Where would I set this I've read various methods on how to set these variables most of which don't seem to work, and I've had to resort to using compiler flags which has a result introduced a whole lot of other problems.:confused: 

What I really need is the deffinitive way to set the LD_LIBRARY_PATH, and to append the PATH variable,so they become globally available.

Thank you in advance for any assistance,

Regards,

---

### Post by hod139 on 2006-03-09
to set LD_LIBRARY_PATH edit 
```

/etc/ld.so.conf

``` 
and add any paths to this file.  After editing run the command 
```

sudo ldconfig

``` to update LD.

For installing Java, I installed using [this]("http://ubuntuforums.org/showthread.php?t=140769&highlight=java") method.  For setting PATHs maybe step 2 will help.

---

