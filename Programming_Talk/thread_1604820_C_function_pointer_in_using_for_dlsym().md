---
title: "C function pointer in using for dlsym()"
date: 2010-10-24
forum: Programming Talk
---

### Post by van7hu on 2010-10-24
Hi all,
I am currently learning a tutorial about library.(Original :[http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html](http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html))
The tutorial is to create a "Dynamically linked shared object libraries",it has 3 sample file as following:
ctest1.c:
> 
void ctest1(int *i)
{
   *i=5;
}  ctest2.c
> 
void ctest2(int *i)
{
   *i=100;
}Using these 2 files to create a library name:libctest.so
Now,the program to use the library is: prog.c
> 
#include <stdio.h> #include <dlfcn.h> 
int main(int argc, char **argv)
 {    
   void *lib_handle;    
   double (*fn)(int *);
   int x;    char *error;
    lib_handle = dlopen("/opt/lib/libctest.so", RTLD_LAZY);
    if (!lib_handle)     
   {       
      fprintf(stderr, "%s\n", dlerror());       exit(1);    
   }
    fn = dlsym(lib_handle, "ctest1");
    if ((error = dlerror()) != NULL)      
   {
        fprintf(stderr, "%s\n", error);       exit(1);    
   }
    (*fn)(&x);    
   printf("Valx=%d\n",x);     
   dlclose(lib_handle);    return 0;
 }                  
This program is compiled and working well.
Now,my question is about the function pointer 'fn' in prog,as I think prog.c calls function ctest1() via function pointer 'fn',here is where I am confused,as ctest1() is defined to return  void ,and *fn is defined to return double,so I think if using them together this way,we'll get warning: 'assignment from incompatible pointer type'. But I don't know why the program worked ?

---

### Post by spjackson on 2010-10-24
> **van7hu said:**
> 
Now,my question is about the function pointer 'fn' in prog,as I think prog.c calls function ctest1() via function pointer 'fn',here is where I am confused,as ctest1() is defined to return  void ,and *fn is defined to return double,so I think if using them together this way,we'll get warning: 'assignment from incompatible pointer type'. But I don't know why the program worked ?
When you compile (and link) prog.c, the compiler knows nothing about ctest1(): there's no function prototype available, and you do not call the function directly.

The magic happens in
```

fn = dlsym(lib_handle, "ctest1");

```If you were assigning the address of a known function, type checking would be possible, but you are not. The address is found **at runtime** and returned via void * which dlsym returns. When data (in this case the address of a function) is passed via void *, no type checking is possible.

---

### Post by van7hu on 2010-10-24
thank spjackson,it makes me  understand more clearly about type checking .

---

