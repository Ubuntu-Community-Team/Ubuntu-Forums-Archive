---
title: "Using ANSI escape characters in Fortran"
date: 2011-09-13
forum: Programming Talk
---

### Post by castiglione on 2011-09-13
Hi - I've been trying to incorporate ANSI escape characters into Fortran but I'm quite at a loss as to how to do so.  I've searched around using Google and the methods I've found which use the:
 
write (*,*) char(27) "[", etc.
 
method don't seem to work using the Fortran 95 compiler using the straight "f95..." command.
 
Where am I going wrong?
 
Thanks in advance!
 
c

---

### Post by gmargo on 2011-09-14
Can you give an example program that you think should work but doesn't?

Here's a quick-n-dirty test program that compiles and runs with **f95**.
It prints "Hello [COLOR=Red]Red[/COLOR] World!".

```

        PROGRAM test
                WRITE(*,'(A,$)')   'Hello '
                WRITE(*,'(A,A,$)') char(27),'[31m'
                WRITE(*,'(A,$)')   'Red'
                WRITE(*,'(A,A,$)') char(27),'[0m'
                WRITE(*,'(A)')     ' World!'
        END PROGRAM test

```

---

