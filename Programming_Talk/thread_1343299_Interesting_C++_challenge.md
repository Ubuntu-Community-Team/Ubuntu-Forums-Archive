---
title: "Interesting C++ challenge"
date: 2009-12-01
forum: Programming Talk
---

### Post by jtrulen on 2009-12-01
Hi all,

I am trying to make a program that will allow me to do the following three things at any point while the program is running:

1.) I need to be able to link in class and implement the class in the program.

2.) I need to be able to compile a class.

3.) I need to be able to unlink a class that is currently linked into the program.

Basically, these three will be done in sequence. I need to first unlink a class, re-compile the class, and re-link the class back in.

I am using C++ for this. Is this possible?

Granted, I know that this will be a major headache if it is at all possible, however if you have any ideas, please point me in the correct direction to take to accomplish this.

Thank you,

Jordan Trulen

---

### Post by johnl on 2009-12-01
I am not sure if this is easily accomplished in C++ due to the fact that the interface for your class may change when it is recompiled, and the calling code must know the size, layout etc.

It is possible to do in a C-manner by implementing the required separate functionality in a shared object (.so), and loading and unloading it dynamically (code untested):


```

/* plugin.c compile with:
 * gcc -Wall -fPIC -c plugin.c -o plugin.o
 * gcc plugin.o -shared -W1,-soname,libplugin.so.1 -o libplugin.so.1.0
 */
#include <stdlib.h>
#include <stdio.h>

void plugin_init(void)
{
    /* do any initialization we need here */
}

void plugin_destroy(void)
{
    /* do any cleanup we need here */
}

void plugin_hello(const char* msg) 
{
    printf("hello from shared library: '%s'\n", msg);
}

```

```

/* main.c compile with gcc -Wall -ldl -o main */
#include <stdlib.h>
#include <stdio.h>
#include <dlfcn.h>

typedef void(*plugin_init)(void);
typedef void(*plugin_destroy)(void);
typedef void(*plugin_hello)(const char*);


int main(int argc, char* argv[])
{
    void* handle = dlopen("libplugin.so.1.0", RTLD_LAZY);
    if (!handle) {
        printf("unable to load shared library\n");
        return 1;
    }

    plugin_init init = dlsym(handle, "plugin_init");
    plugin_destroy destroy = dlsym(handle, "plugin_destroy");
    plugin_hello hello = dlsym(handle, "plugin_hello");

    if (!init || !destroy || !hello) {
        printf("unable to locate required entry points\n");
        dlclose(handle);
        return 1;
    }

    /* call into the shared library */
    init();
    hello("hello world");
    destroy();
 
    dlclose(handle);   

    /* here we could fork()/exec() to gcc/ld and rebuild the
     * shared library, then reload it with dlopen() again.
     */

    return 0;
}

```

---

### Post by jtrulen on 2009-12-02
Thank you much. That worked as I wanted.

---

