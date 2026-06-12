---
title: "Linker ld"
date: 2013-05-29
forum: Programming Talk
---

### Post by adityaharish on 2013-05-29
I wrote a test file to check whether my gcc is correctly working or not .

My file is just this thing

test.c
```
#include<stdio.h>
int main()
{
printf("THIS is a C-file\n");
return 0;
}
```

When I try to compile the file, it shows the following error.


```
shraddesh@shraddesh-Samsung-Desktop-System:~$ vi test.c
shraddesh@shraddesh-Samsung-Desktop-System:~$ gcc test.c
/usr/bin/ld: this linker was not configured to use sysroots
collect2: error: ld returned 1 exit status
shraddesh@shraddesh-Samsung-Desktop-System:~$ 
```


So please help me in solving this problem and make my gcc run properly ..

---

### Post by lisati on 2013-05-29
*Thread moved to **Programming Talk**.*

---

### Post by Bachstelze on 2013-05-29
How did you install gcc?

---

### Post by adityaharish on 2013-05-30
I think the problem is not with gcc ...
I installed gcc using synaptic package manger
It worked for few hours after I installed.
When I updated  **ld** , **binutils**  the above error cropped up .

---

### Post by Bachstelze on 2013-05-30
Which packages exactly did you install? If you installed only the package *gcc*, try installing *build-essential*. Also, are you using third-party repositories?

---

### Post by adityaharish on 2013-05-30
Solved it .. I completely uninstalled  gcc , g++ and binutils and re-installed them using synaptic package manager.

Now It's working

---

