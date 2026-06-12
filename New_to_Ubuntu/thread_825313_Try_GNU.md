---
title: "Try GNU"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Nam Ninh on 2008-06-10
Hi ;

After installing Ubuntu, I tried to run a simple C program for testing but I got a complier errors. I assume GNU compiler is already included in linux. 

Did I miss any thing??





#include <stdio.h>
#include <string.h>

main()
{
   printf("Hello\n");
}

gcc test.c


test.c:1:19: error: stdio.h: No such file or directory
test.c:2:20: error: string.h: No such file or directory
test.c: In function ‘main’:
test.c:6: warning: incompatible implicit declaration of built-in function ‘printf’

---

### Post by jrusso2 on 2008-06-10
did you install the build-essential package?

---

### Post by Joeb454 on 2008-06-10
From the terminal run ```
sudo apt-get install build-essential
``` And then try again

---

### Post by Linux_Man on 2008-06-10
GCC isn't installed by default in Ubuntu, install the build-essential package.

---

### Post by LibertyShadow on 2008-06-10
Have you installed the package build-essential?

```
sudo apt-get install build-essential
```

It's got handy dev tools.

---

### Post by iaculallad on 2008-06-10
Try to install the required files first: 

:Build-essential files 
```
sudo apt-get install build-essential
``` :[libc6-dev]("http://packages.ubuntu.com/edgy/libdevel/libc6-dev"), and [manpages-dev]("http://packages.ubuntu.com/edgy/doc/manpages-dev") files.

---

### Post by Nam Ninh on 2008-06-10
> **iaculallad said:**
> Try to install the required files first: 

:Build-essential files 
```
sudo apt-get install build-essential
``` :[libc6-dev]("http://packages.ubuntu.com/edgy/libdevel/libc6-dev"), and [manpages-dev]("http://packages.ubuntu.com/edgy/doc/manpages-dev") files.


It works.
After compiling test.c, An execute object (a.out) is created.

Now. How to run the program?. The command: a.out does not work.


Thanks.

---

### Post by KingTermite on 2008-06-10
Silly, I know, but "." (current directory) is not in your path.

type ./a.out


I added "." to my PATH in my .bashrc file to try to alleviate this issue.

---

