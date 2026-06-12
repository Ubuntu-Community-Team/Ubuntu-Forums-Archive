---
title: "[SOLVED] Continue process after SSH session has closed"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by radiocognition on 2008-07-11
Hey everyone,

I really should know the answer to this one, but I haven't been able to figure out how to do it.

I have this program that I need to run on an Ubuntu server where I work.  Its doing some serious computational work - and sometimes takes up to two or three days to complete.  Whenever I execute the program from ssh, everything runs fine, but when I close my session, the server stops the process.  Is there a way to force the server to continue running the job even after I close the ssh session?

Also, is there a way to have the computer notify me when the job is finished?

Right now I am doing this:
```
 user@somebigmachine $   biglongprogram && echo "Your Job has Finished" > finished.txt
```

---

### Post by quantumstitch on 2008-07-11
check this.
[http://ubuntuforums.org/archive/index.php/t-500711.html](http://ubuntuforums.org/archive/index.php/t-500711.html)
peace,
stitch

---

### Post by radiocognition on 2008-07-11
Awesome, why didnt I see that thread earlier?

---

### Post by hyper_ch on 2008-07-11
use "screen" --> [http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)

---

