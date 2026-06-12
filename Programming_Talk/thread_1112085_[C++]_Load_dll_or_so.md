---
title: "[C++] Load dll or so"
date: 2009-03-31
forum: Programming Talk
---

### Post by djbushido on 2009-03-31
Is there a definite way to load an so file (preferably also dll)? Code I found online is extremely difficult to understand and example code doesn't compile. Thanks!

---

### Post by dwhitney67 on 2009-03-31
You will need to be more specific about your problem.  Typically an application will load the shared-object library when needed, presuming of course it was linked to use it.

Some issues arise when the application cannot find the shared-object library because the path is either not defined in /etc/ld.so.conf (or other related area) or not defined in LD_LIBRARY_PATH.

I can help you, but as I stated earlier, you will need to be more specific with your problem.

---

### Post by johnl on 2009-03-31
If you want to dynamically load a library, you should take a look at the dl* functions in <dlfcn.h>, specifically:

```

/* load a dynamic library into memory */
void *dlopen(const char *filename, int flag);
/* return the address of the specified symbol */
void *dlsym(void *handle, const char *symbol);

```

This is of course, for Linux.  Windows has a separate but similar set of functions -- LoadLibrary() and GetProcAddress().

---

### Post by djbushido on 2009-03-31
as far as i know, the functions should be:
[PHP]int main(){
void *handle = dlopen("libexample.so",RD_LAZY);
void *function = dlsym(*handle, example_function);
//then do i just do
function();[/PHP]
Right? Only, it doesn't work.  An example code for a .so would be
[PHP]
int main(){
printf("hello world!");
return 0;
}[/PHP]
Thanks for your help!

EDIT:
so here is the code specifically that I am trying to compile.
library.cpp:
```
#include <iostream>
using namespace std;
int main()
{
        cout << "hello world!";
        return 0;
}
```

and the program to execute it:
execute.cpp
```
#include <dlfcn.h>
using namespace std;
int main()
{
        void *handle = *dlopen("libexample.so",RD_LAZY);
        void *function = *dlsym(*handle,"main");
        *function();
        return 0;
}


```
I can compile the library fine with: "gcc -shared -o libexample.so library.cpp" and with a -ldl flag as well, but compiling the program with "gcc -o execute execute.cpp" returns this error: ```
execute.cpp: In function &#8216;int main()&#8217;:
execute.cpp:5: error: &#8216;RD_LAZY&#8217; was not declared in this scope
execute.cpp:6: error: &#8216;void*&#8217; is not a pointer-to-object type
execute.cpp:7: error: &#8216;function&#8217; cannot be used as a function
```

---

### Post by nvteighen on 2009-03-31
Well, you should compile with the -ldl flag to link to the dynamic loader's library...

And also, a library should never have a main() method... Look here to learn how to build libraries: [http://crasseux.com/books/ctutorial/Building-a-library.html](http://crasseux.com/books/ctutorial/Building-a-library.html)

---

### Post by djbushido on 2009-03-31
This looks like it should work. Will try and post back results. BTW - you're located at the origin???

---

### Post by johnl on 2009-03-31
Almost got it.  You don't need to mess with dereferencing the void pointer handles -- just pass the pointer to the dl() functions.

Also, you can use a typedef to tell c++ what the function you are looking for is supposed to accept/return:
```

/* suppose the function we are looking for is:
 *  int addints(int a, int b)
 * declare a type 'addints_ptr' that is a pointer
 * to a function matching this signature.
 */
typedef int(*addints_ptr)(int,int);

int main(int argc, char* argv[])
{
  /* open the library */
  void* handle = dlopen("foo.so", RTLD_LAZY);
  
  if (!handle) {
     cout << "failed to open library" << endl;
     return 0;
  }
  /* resolve the symbol 'addints' */
  addints_ptr addints = (addints_ptr)dlsym(handle, "addints")

  if (!addints) {
     cout << "failed to resolve symbol" << endl;
  } else {
     cout << "3+4=" << addints(3, 4) << endl;
  }
  /* clean up */
  dlclose(handle);
}

```

---

### Post by dwhitney67 on 2009-03-31
Why would anyone go through the trouble of loading a DLL programatically?  I've never seen this done in any of the projects I have supported; but I suppose there must be some rationale to it.  Can someone explain?

---

### Post by cabalas on 2009-04-01
A friend of mine uses this technique when he write game engines to modularize his code, once he has designed the interface it allows him to swap and test different rendering engines without having to recompile the whole app, or for his windows builds it allows him to swap between the directX version and the openGL version easily.

---

### Post by dwhitney67 on 2009-04-01
> **cabalas said:**
> A friend of mine uses this technique when he write game engines to modularize his code, once he has designed the interface it allows him to swap and test different rendering engines without having to recompile the whole app, or for his windows builds it allows him to swap between the directX version and the openGL version easily.

Great, thanks for the explanation.

---

### Post by johnl on 2009-04-01
A really common usage for this sort of thing is implementing plugins.  Generally you'll have a standard API that a plugin should provide, and upon loading the library pass a bunch of function pointers into the plugin, allowing it to access the main program's code.

---

### Post by WitchCraft on 2009-04-01
> 
execute.cpp:5: error: &#8216;RD_LAZY&#8217; was not declared in this scope
Shouldn't that be be RTLD_LAZY


[COLOR=DarkOrange]**#define _GNU_SOURCE**[/COLOR]
#include <dlfcn.h>



Additionally instead of WinMain in windows, you can use:
```

void __attribute__((constructor)) OnLoad()
void __attribute__((destructor)) OnUnLoad()

```Moreover:
```

__attribute__ ((visibility ("protected")))
__attribute__ ((visibility ("hidden")));

```to make reverse-engineering harder.


and 
```

#if (defined(__GNUC__) )
    #ifndef __stdcall 
        #define __stdcall __attribute__((stdcall)) 
    #endif 
#endif 


#define WINAPI      __stdcall
#define APIENTRY    WINAPI
#define APIPRIVATE  __stdcall
#define CALLBACK    __stdcall
#define PASCAL      __stdcall

```

---

### Post by djbushido on 2009-04-05
now compiling this code: ```
#include <iostream>
#include <string>
#include <dlfcn.h>

using namespace std;

unsigned long square(int num1);
typedef int(*hello_ptr)();
int main()
{
    string test = "hello world!";
    cout << test << endl;
    cout << square(4);



  /* open the library */
  void *handle = dlopen("libexample.so", RTLD_LAZY);

  if (!handle) {
     cout << "failed to open library" << endl;
     return 0;
  }
  /* resolve the symbol 'addints' */
  hello_ptr hello = (hello_ptr)dlsym(handle, "hello_world");

  if (!hello) {
     cout << "failed to resolve symbol" << endl;
  } else {
     hello();
  }
  /* clean up */
    return 0;

}

unsigned long square(int num1)
{
    return (num1 * num1);
}

```
returns an error of: ```
obj/Debug/main.o||In function `main':|
/home/brad/Programming/Test/main.cpp|18|undefined reference to `dlopen'|
/home/brad/Programming/Test/main.cpp|25|undefined reference to `dlsym'|
||=== Build finished: 2 errors, 0 warnings ===|

```
Any ideas? I placed "libexample.so" in all folders, and was compiled with gcc and the -shared option.

---

### Post by dwhitney67 on 2009-04-05
Don't forget to specify the -ldl.

---

### Post by djbushido on 2009-04-05
I did in compiling. Pretty sure. I'll try again and see what happens.
EDIT: Output:```
 gcc -o main main.cpp -ldl
/tmp/ccypg5K1.o: In function `__static_initialization_and_destruction_0(int, int)':
main.cpp:(.text+0x29): undefined reference to `std::ios_base::Init::Init()'
main.cpp:(.text+0x2e): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccypg5K1.o: In function `main':
main.cpp:(.text+0x82): undefined reference to `std::allocator<char>::allocator()'
main.cpp:(.text+0x9c): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(char const*, std::allocator<char> const&)'
main.cpp:(.text+0xa7): undefined reference to `std::allocator<char>::~allocator()'
main.cpp:(.text+0xb5): undefined reference to `std::cout'
main.cpp:(.text+0xba): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <char, std::char_traits<char>, std::allocator<char> >(std::basic_ostream<char, std::char_traits<char> >&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
main.cpp:(.text+0xc2): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
main.cpp:(.text+0xca): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
main.cpp:(.text+0xe3): undefined reference to `std::allocator<char>::~allocator()'
main.cpp:(.text+0x10b): undefined reference to `std::cout'
main.cpp:(.text+0x110): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(unsigned long)'
main.cpp:(.text+0x13c): undefined reference to `std::cout'
main.cpp:(.text+0x141): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
main.cpp:(.text+0x149): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
main.cpp:(.text+0x151): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
main.cpp:(.text+0x185): undefined reference to `std::cout'
main.cpp:(.text+0x18a): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
main.cpp:(.text+0x192): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
main.cpp:(.text+0x19a): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
main.cpp:(.text+0x1c1): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
main.cpp:(.text+0x1dd): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/tmp/ccypg5K1.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

---

### Post by djbushido on 2009-04-05
Problem Fixed!
Changing compiling to "g++" instead of gcc fixed it.
Thanks all!

---

