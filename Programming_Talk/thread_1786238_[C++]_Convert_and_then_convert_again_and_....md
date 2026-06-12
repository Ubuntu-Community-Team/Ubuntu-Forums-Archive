---
title: "[C++] Convert and then convert again and ..."
date: 2011-06-19
forum: Programming Talk
---

### Post by sakishrist on 2011-06-19
Hello everybody,

I am having a problem (or lots of that type) finding a working way to convert some char(s) to Bytef type (used by the zlib). 

I am kind of new to C++ programing and syntax so I might be missing something obvious. 

Anyhow, here is my program:```
#include <iostream>
#include <zlib.h>

using namespace std;

void _compress(unsigned char & in_data, size_t in_size, unsigned char & out_data, size_t out_size){

z_stream z;

int status;

    z.avail_in = 0;
    z.next_out = &out_data;
    z.avail_out = out_size;

        if ( z.avail_in == 0 ) {
            z.next_in = &in_data;
            z.avail_in = in_size; //dfjngdfng
        }
        if ( z.avail_in != 0 )
            status = deflate( &z, Z_NO_FLUSH );
        int count = out_size - z.avail_out;

} 



int main(){
    unsigned char a[100];//13
    a=reinterpret_cast<unsigned char>("Hello world!");
    unsigned char b[100];
    _compress(*b,13,*b,100);
    cout << b << endl;
    return 0;
}
```

My goal is to make an easy-to-use function that will compress (and later de-compress) a buffer. 

The error I get with this last compilation attempt is: ```
sakishrist@sakishrist-laptop:~/Desktop/c++/zlib$ g++ zlib.cpp -o zlib_c -lz
zlib.cpp: In function ‘int main()’:
zlib.cpp:42:50: error: cast from ‘const char*’ to ‘unsigned char’ loses precision
zlib.cpp:42:50: error: incompatible types in assignment of ‘unsigned char’ to ‘unsigned char [100]’

```

I tried many different things but all of them fail. I think (I can be wrong with so many errors) that I know how to use * and & in general.

I hope you can give me a piece of advice. :)

Thanks in advance!!!

---

### Post by ziekfiguur on 2011-06-19
It's going wrong here:
```
    unsigned char a[100];//13
    a=reinterpret_cast<unsigned char>("Hello world!");
```
First you define a as an array of 100 chars. 
Then you have a string, and reinterpret it as an unsigned char and try to assign that to the array.
In C++ it's impossible to assign anything to an array, only to places in an array. However, if you want the character array to be the same as the string, you have to do it one character at a time, like this:
```

unsigned char a[100];
std::string hello = "Hello world!";
for (size_t i = 0; i < 100; ++i)
    a[i] = i < hello.size() ? hello[i] : 0;

```
or at definition time, like this:
```
unsigned char a[] = "Hello world!";

```

Also, in C++ "Hello world!" is actually a pointer to an array of characters terminated by a 0 byte. If you reinterpret the pointer (which is 4 or 8 bytes long depending on your processor type) to a char which is 1 byte long, you drop 3 or 7 bytes, that is what the compiler is complaining about.

---

### Post by sakishrist on 2011-06-19
Hi again and thanks a lot for the reply,

I did the character assignment as you suggested. Leaving everything else as is seems to be OK for the compiler but when trying to run the program I get an error reading "Segmentation Fault". From past experience I think this means that my program is trying to access memory that is "out of reach" ... or outside of the assigned for the program, but again, I am not sure.

Thanks again! :)

---

### Post by ziekfiguur on 2011-06-19
there are a couple more errors in your program.
First of all, you are passing b twice to _compress instead once a and once b.
Second, _compress takes two references to pointers, and you pass two normal characters (An array variable is a memory address, like a pointer, *b dereferences that address and passes the first character in the array) of which C++ automatically takes a reference. in the line `            z.next_in = &in_data;' you take the memory address of that reference and put that into a stream object. I am not familiar with zlib, but i'm quite sure that is not what you're supposed to do.

You could try to fix this by trial and error, but I would seriously recommend you to read up on pointers and arrays, what they are, how they work and how the * and & operators in C and C++ work. 
Because i'm getting a feeling you are used to higher level languages and don't really know what you are doing here.
You can find a good tutorial [here]("http://www.cplusplus.com/doc/tutorial/") and another one [here]("http://www.cprogramming.com/tutorial.html") though it would probably be best to get a good book on C++

---

### Post by sakishrist on 2011-06-19
You are quite right, about both that I am used to a higher level language and that I still struggle to grasp the idea of pointers.

I've been going through pointers quite a lot of times but I still don't understand why my compiler even allows me to compile such code:```
#include <iostream>

using namespace std;

void func(char *a){
    
    cout << "Inside:" << endl;
    cout << a << endl;
    cout << *a << endl;
    cout << &a << endl;
    
}

int main(){
    char a[100] = "Hello world!";
    func(a);

    cout << "Outside:" << endl;
    cout << a << endl;
    cout << *a << endl;
    cout << &a << endl;
    return 0;
}
```And I can't really understand what is being passed on to the function.

But anyhow, I know the best thing to do is do some more reading ... but, I'd be grateful if you could answer just this one question: Doesn't * (when not declaring) mean "take the value from this address", * (when declaring) - "this is an address" and & -  "take the address of this object"?

Does * mean something else for arrays?

The above code just demolishes these ideas of mine. 

Anyway, thanks a million for the links and for the assistance!

---

### Post by Petrolea on 2011-06-19
Ah, pointers. I'd recommend you to read this, it explains how they work pretty good: [http://pw1.netcom.com/~tjensen/ptr/pointers.htm](http://pw1.netcom.com/~tjensen/ptr/pointers.htm)

You will see examples for arrays, strings, structs and so on.

---

### Post by sakishrist on 2011-06-19
Thanks a lot!!! ;)

---

### Post by ziekfiguur on 2011-06-20
> **sakishrist said:**
> but, I'd be grateful if you could answer just this one question: Doesn't * (when not declaring) mean "take the value from this address", * (when declaring) - "this is an address" and & -  "take the address of this object"?

Does * mean something else for arrays?

This is partly right. When declaring:
* means "this is a pointer", you had that right
& means "this is a reference"
When not declaring:
* means "take the value that this pointer points to"
& means "take the address of this variable"

For arrays, * means the same as for a pointer. An array variable is basically a constant pointer. That means that you cannot assign another variable to an array, only to the places in the array, to do that you can use the usual brackets like `a[0] = 3; a[23] = 56;' or you can use * like this: `*a = 3; *(a + 23) = 56;'

Also, please note that the tutorial that Petrolea mentioned is about C, not C++ and will not discuss references, which are like pointers but behave differently.

---

