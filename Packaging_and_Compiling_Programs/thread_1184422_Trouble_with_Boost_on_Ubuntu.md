---
title: "Trouble with Boost on Ubuntu"
date: 2009-06-11
forum: Packaging and Compiling Programs
---

### Post by pjvdm on 2009-06-11
Hi,

I'm trying to compile this simple "program" using boost 1.43 under ubuntu (intrepid):

     ```
#include <boost/tr1/memory.hpp>

int main()
{
    return 1234;
} 
```However, I get the following error:     
```
 /usr/include/boost/tr1/detail/config.hpp:60:26: error: no include path in which to search for utility 
```The boost website says ([here]("http://www.boost.org/doc/libs/1_35_0/doc/html/boost_tr1/usage.html#boost_tr1.usage.include_style")) to fix this, either     
    ```
 #define BOOST_TR1_DISABLE_INCLUDE_NEXT 
``` or     
     ```
#define BOOST_TR1_GCC_INCLUDE_PATH /usr/include/c++/4.2 
``` but neither works. Both combined also won't work. It still outputs the same error.

I compile with the following command:  
```
      g++ -v test.cpp -DBOOST_TR1_DISABLE_INCLUDE_NEXT -DBOOST_TR1_GCC_INCLUDE_PATH=/usr/include/c++/4.3 -I /usr/include/boost/tr1/tr1 -I /usr/include/boost -o test 

```My gcc include order is as follows which looks correct according to the boost docs:

```

#include <...> search starts here:
 /usr/include/boost/tr1/tr1
 /usr/include/boost
 /usr/include/c++/4.3
 /usr/include/c++/4.3/i486-linux-gnu
 /usr/include/c++/4.3/backward
 /usr/local/include
 /usr/lib/gcc/i486-linux-gnu/4.3.2/include
 /usr/lib/gcc/i486-linux-gnu/4.3.2/include-fixed
 /usr/include
End of search list.

```I've also tried to move the /usr/include/boost dir to another location such as /usr/local/include, but got the same result.

Does anybody know how to fix this in Ubuntu? 

cheers,
Pieter

---

### Post by pjvdm on 2009-06-11
OK, I copied all the boost includes to another non-std location like ***/home/<myusername>/boost***.

Now it compiles using the following:

```
g++ test.cpp -I/home/<myusername>  main.cpp -o test
```I this the only way you can get boost going on Ubuntu, by referring to copy of the boost includes, located in a place other than*** /usr/include*** or ***/usr/local/include***?

Thx.

Pieter

---

### Post by matcatc on 2009-07-05
It works for me just having it in /usr/include. I just installed the boost-dev libraries from synaptic and thats where they automatically installed.

I should note that i586-mingw32msvc-gcc (mingw) doesn't seem to find it there. Its possible (and I'm trying to figure it out) that you have to install boost in a special place for mingw separate from normal gcc/g++

EDIT: to use boost w/ i586-mingw32msvc-gcc, you need to install the boost libraries in the i586-mingw32msvc-gcc directory (/usr/ i586-mingw32msvc-gcc). In order to get the lib files to work (.a and .so) I had to download bjam and the boost package (from boost directly). I compiled the libraries according to the getting_started page that comes in the package (start from index.html, click getting started, click  [Getting Started on Unix variants ...]("file:///home/matcat/Desktop/boost_1_39_0/more/getting_started/unix-variants.html"))).

---

