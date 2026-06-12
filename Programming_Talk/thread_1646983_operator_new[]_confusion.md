---
title: "operator new[] confusion"
date: 2010-12-16
forum: Programming Talk
---

### Post by Lord DEA on 2010-12-16
Hi every1,

please explain how the operator new[] works here:
```

int main(){
    char *a;
    a = new char[6];
    int b = strlen(a); //why do i get b = 24??
    return 0;
}

```

shouldn't I get b = 6?

---

### Post by dwhitney67 on 2010-12-16
strlen() counts the number of bytes in a string until a null-terminating character is found.

You are attempting to deduce the length of a string for which you have not initialized with any data; thus coincidentally, the null-character in your string is located at the 25th byte.

Btw, might it not be better to use an STL string?


P.S. strlen() returns a size_t, not an int.  It is best that you define the appropriate type for 'b'.

---

### Post by Lord DEA on 2010-12-16
> **dwhitney67 said:**
> strlen() counts the number of bytes in a string until a null-terminating character is found.

You are attempting to deduce the length of a string for which you have not initialized with any data; thus coincidentally, the null-character in your string is located at the 25th byte.

but how come I get the same 24 every time I compile and run? what are the odds?
I get this when using Visual c++, but when using GCC I get 3...
Please explain a little further here...

> 
Btw, might it not be better to use an STL string?

I'm trying to load a text file into memory. which way is better (STL string or char*)?
The problem I'm getting is that I get a lot of garbage, besides the actual contents of the file...

Thanks a lot for your help

---

### Post by MadCow108 on 2010-12-16
the behavior is undefined but not necessarily non-deterministic
It is not unusual that you often or even always receive the same result.

many parts of the virtual memory of a process get zeroed on creation (e.g. bss section), the compiler may choose to zero padding bytes allocated for memory access alignment purposes, zero terminate char arrays blocks for security reasons, the memory allocator management structure may contain a zero at the 24th byte for this kind allocation, ...

all very implementation dependent

you should use string's when possible, especially when you are inexperienced you are likely to make mistakes which the string class avoids for you (like memory management)

---

### Post by dwhitney67 on 2010-12-16
> **Lord DEA said:**
> 
The problem I'm getting is that I get a lot of garbage, besides the actual contents of the file...


The following code snip can be used to print every line in a text file:
```

std::ifstream file("filename.txt");

if (file)   // test that the file has been opened
{
   std::string line;   // used for storing a line from the file

   while (std::getline(line, file))   // read one line at a time
   {
      std::cout << line << std::endl;   // display result
   }
}

```

---

### Post by Lord DEA on 2010-12-17
Ok, I'm good whith the strlen part, but check this:
```

#include <iostream>
#include <fstream>

using namespace std;

int main(){
    ifstream file;
    char *buffer;
    int length;
    
    file.open("in.txt", ifstream::ate);
    if (!file.good()) return -1;
    length = file.tellg();
    file.seekg(0,ios_base::beg);
    cout << "file length: " << length << endl;
    buffer = new char[length];
    file.read(buffer, length);
    file.close();
    cout << buffer;
    getchar();
    return 0;
    
}

```
and you have this in.txt:
```
this is a test
```

the length of the file is 14 characters, which is printed ok, but when the buffer is printed, aditional garbage is printed...

I want to use a char pointer and not a string object for the buffer, since that would make things a little bit too easy.

what would be a propper solution for this?

(I know I can put a NULL character to prevent garbage from being printed, but am looking for a more 'neat' solution..)

thanks for all your help guys

---

### Post by rex_virtutis on 2010-12-17
I think you need to allocate an extra byte for the null terminator so you don't lose the last char in the buffer.
```
buffer = new char[length + 1];
```

From there you could do 
```
buffer[length] = 0;
```
or you could initialize the buffer to zero before you fill it, like:
```
memset(buffer, 0, length + 1);
```

I'm not too familiar with using "new" to allocate arrays, since I prefer to use C functions for strings and buffers but it looks as though you are leaking memory. It's good practice to always free your heap  allocated memory.
```
delete[] buffer;
```

---

### Post by nvteighen on 2010-12-17
Cases like this should make everyone aware that one of the good C++ features is the std::string class, which is also a nice simple class to start learning the STL in general.

But ok, yes, you always have to allocate space for the '\0' character. But this isn't a problem of new[]... the same goes for C malloc()...

---

### Post by Lord DEA on 2010-12-17
Thx for all ur help guys.
But all of that brought another question. Lest say I do this:

```

char *buffer;
buffer = new char[12]
strcpy(buffer, "hello world");
buffer[5] = '\0';
delete[] buffer;

```

Does the delete[] operation free the whole memory block? or it also looks for a null terminator?. In case it does free the whole block, how does it know what size the buffer has?

---

### Post by MadCow108 on 2010-12-17
it frees the whole block, the allocator does not care what for data is in the block of memory

how this is handled depends on the allocator used. It may not even need to know how big the block actually was, and if it does it will writes this information somewhere in in its internal data (or attaches it to the start/end of the block)

and no there is no reliable way to get this information from the allocator (and you should never need it in the first place)

---

### Post by dwhitney67 on 2010-12-17
> **Lord DEA said:**
> Thx for all ur help guys.
But all of that brought another question. Lest say I do this:

```

char *buffer;
buffer = new char[12]
strcpy(buffer, "hello world");
buffer[5] = '\0';
delete[] buffer;

```

Does the delete[] operation free the whole memory block? or it also looks for a null terminator?. In case it does free the whole block, how does it know what size the buffer has?

Obviously you are not working on some embedded software to activate "una bomba intelligente contra la FARC".

Thus I would recommend that in lieu of what you have posted above, that you focus on the following for C++ applications:
```

#include <string>

...


std::string buffer = "Hola Mundo";

```
There's no need to explicitly allocate memory, and when 'buffer' goes out of scope the heap memory it allocates will be destroyed (for your convenience).

P.S.  If you are learning about allocation in general, then please forgive "mis comentos sarcasticos."

---

### Post by Lord DEA on 2010-12-19
Whether it works or not, is actually not important for me. I'm trying to understand HOW it works (And I think I do now), and hence the need to use a char pointer instead of a string object.
thx for all your help people, really appreciated.

---

### Post by worksofcraft on 2010-12-19
> **Lord DEA said:**
> Whether it works or not, is actually not important for me. I'm trying to understand HOW it works (And I think I do now), and hence the need to use a char pointer instead of a string object.
thx for all your help people, really appreciated.

+1
What you have explored here applies equally to arrays of any kind of data, not just strings.

There are some other things you should know about operators new and delete and in particular if you delete an array of objects that have destructors you should tell delete that it is an array or it may not do quite what you want.

[php]
    some_class pArray = new pArray[50];
    delete [] pArray;
[/php]
Those empty brackets after delete are necessary!

---

