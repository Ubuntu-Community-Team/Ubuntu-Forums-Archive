---
title: "question regarding LD_PRELOAD"
date: 2013-01-16
forum: Programming Talk
---

### Post by IAMTubby on 2013-01-16
Hello,
I was reading about LD_PRELOAD and LD_LIBRARY_PATH and came to know that on doing export LD_PRELOAD=/home/path/to/libmylib.so, it loads the libmylib.so before loading any other library.
 
I have three questions:
1.How is -L different from LD_PRELOAD and LD_LIBRARY_PATH ?
**Probable answer :**-L links at link time while LD_PRELOAD and LD_LIBRARY_PATH at run time. I just need some confirmation on this.

2.Can I say that doing 
**LD_PRELOAD=/path/required/libmylib.so ./a.out** is same as
**copying the required .so to one of the folders mentioned in LD_LIBRARY_PATH ?** that is,
```
    
$cp libmylib.so /home/mypath/library
$gcc -Wall -L/home/mypath/library -lmylib -o exe
$export LD_LIBRARY_PATH=/home/mypath/library
$./a.out

```
3.In the LD_LIBRARY_PATH way of doing things, in the link stage itself,(**$gcc -Wall -L/home/mypath/library -lmylib -o exe**), you are mentioning that the shared object called libmylib resides in /home/mypath/library, and then the exe is created. 
Then why can't the exe **run** taking the shared object from here. Why do we again have to do $export LD_LIBRARY_PATH=/home/mypath/library before running the executable ?

Thanks.

---

