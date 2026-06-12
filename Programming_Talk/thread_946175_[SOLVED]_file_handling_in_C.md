---
title: "[SOLVED] file handling in C"
date: 2008-10-13
forum: Programming Talk
---

### Post by polarbear12345 on 2008-10-13
i m unable to use file handling commands in c in ubuntu
eg open(),read(),write(),close(),lseek() etc are not working


is there any package i need to install for it ????
similarly fork() is also not working

---

### Post by Orange_and_Green on 2008-10-13
(I'd suggest this is moved to Programming Talk... anyway...)

Hi polarbear, here's a quick checklist:

1) make sure the compiler and libraries are installed:
```
sudo apt-get install gcc libc6-dev
```

2) make sure you are including stdio at the top of your .c file or in your header file (#include <stdio.h>)

Furthermore, what is it that's not working? Do you get a compile error? Do you get a link error? Or do you compile fine and the binary just doesn't do what you'd expect it to do? Could you post gcc's output please?

---

### Post by polarbear12345 on 2008-10-13
#include<stdio.h>
int main()
{

        int fd=open("data.txt",O_CREAT|O_RDWR,0777);
        if(fd==-1)
                printf("error");
        write(fd,"dear",4);
}

i tried above simple program
on compiling it gave

test.c: In function &#8216;main&#8217;:
test.c:5: error: &#8216;O_CREAT&#8217; undeclared (first use in this function)
test.c:5: error: (Each undeclared identifier is reported only once
test.c:5: error: for each function it appears in.)
test.c:5: error: &#8216;O_RDWR&#8217; undeclared (first use in this function)

---

### Post by WW on 2008-10-13
O_CREAT and related macros are defined in the header file fcntl.h, so add the line
```

#include <fcntl.h>

```
to the beginning of your program.

---

### Post by polarbear12345 on 2008-10-13
thankkkkkkk u very much .....its working

---

### Post by slavik on 2008-10-13
> **polarbear12345 said:**
> thankkkkkkk u very much .....its working
1 more thing 
is there any way i can see the declarations of functions and constants in a header file
by opening the files and reading them ... :)

---

### Post by dwhitney67 on 2008-10-13
polarbear12345 -

Install the man-pages.  That way you can reference what (header file) dependencies are for any particular C-library function you are trying to use.

Here's how:
```
sudo apt-get install manpages-dev
```

Then use the man-pages.  For example:
```

man -aw open     # show all man-pages for open
man 2 open       # show man-page for C-library open

```

---

