---
title: "loading shared library in C"
date: 2009-04-14
forum: Programming Talk
---

### Post by delirejisor on 2009-04-14
Hi, I'm trying to load a .so file to my .c file.
I'm doing it like this.

```

#include <stdio.h>
#include <dlfcn.h>

int main() {
    void* handle = dlopen("./libmystuff.so", RTLD_LAZY);
    
    if (!handle) {
        return 1;
    }
    
    typedef void (*hello_t)();

    dlerror();
    hello_t hello = (hello_t) dlsym(handle, "Function2");
    const char *dlsym_error = dlerror();
    if (dlsym_error) {
        dlclose(handle);
        return 1;
    }
    hello();
    
    dlclose(handle);
}

```

But i dont want to use function name (which is "Function2" in this example)  in dlsym, I want to get all the functions in the .so file whatever its name is.
I assume signatures of functions are same at .so file.

Is there a way to do it?
Thanks

---

