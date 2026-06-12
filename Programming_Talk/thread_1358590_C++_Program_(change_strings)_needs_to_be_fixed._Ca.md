---
title: "C++ Program (change strings) needs to be fixed. Can anyone help?"
date: 2009-12-18
forum: Programming Talk
---

### Post by OVERPOWER8 on 2009-12-18
I have written a program on C++, that change value of strings *Name1* and *Name2*. 
It is compiling, but launching with an error: "Segmentation fault".

Program must be with pointers and with one extra function:

```

#include <iostream>
#include <string.h>
using namespace std;
 
void StringChange(char* init, char* dest)
{
        char* temp;
        *temp = *init;
        *init = *dest;
        *dest = *temp;
}
 
int main()
{
        char* Name1 = "Winona";
        char* Name2 = "Boris";
        
        StringChange(Name1, Name2);
        
        puts(Name1);
        cout << endl;
        
        puts(Name2);
        cout << endl;
}

```Btw, do you mind if I ask some C++ questions here?

---

### Post by unknownPoster on 2009-12-18
if you are using C++, why not use the string data type instead of dealing with C-style strings?

---

### Post by OVERPOWER8 on 2009-12-18
I solved myself: :)

That's how it should look like: 

```
#include <iostream>
#include <string.h>
using namespace std;
 
void StringChange(char** init, char** dest)
{
        char* temp;
        temp = *init;
        *init = *dest;
        *dest = temp;
}
 
int main()
{
        char* Name1 = "Winona";
        char* Name2 = "Boris";
        
        StringChange(&Name1, &Name2);
        
        puts(Name1);
        cout << endl;
        
        puts(Name2);
        cout << endl;
}
```

>> [COLOR=Black]**[unknownPoster]("http://ubuntuforums.org/member.php?u=845681")**[/COLOR]
That's the task

---

### Post by Linteg on 2009-12-18
> **OVERPOWER8 said:**
> I solved myself: :)
That's how it should look like
It works, yes, but I am not sure that you understand what is happening (which is essential when it comes to pointers).
As pointers are not that trivial I would recommend you to have a look at a tutorial such as [this](http://www.youtube.com/watch?v=UvoHwFvAvQE) or [this](http://home.netcom.com/~tjensen/ptr/pointers.htm) to gain a little more understanding.

---

### Post by Some Penguin on 2009-12-18
You're not changing the values of the strings; you're changing the pointers to the strings.   There's a fundamental difference.  It would not surprise me if the intention is for you to change the actual contents at those memory addresses rather than merely swap the addresses.

---

### Post by Can+~ on 2009-12-18
Let's say you have to websites A, and B owned by your company. But your boss now tells you that website [http://comapny.a.com](http://comapny.a.com) should link to B and [http://comapny.b.com](http://comapny.b.com) should link to A.

The difference lies between: changing the data would imply to move all the .html/.php/whatever files from one server/folder to another. Or, rename the sites and correct the URLs so you don't need to move anything, just the references.

Also, read on C++ Strings.

---

### Post by kwyto on 2009-12-18
i don't understand why aren't you using c++ strings, that's the whole point they were created in c++, because in c "char" were messy and difficult to work with. besides, this is a simple program, don't make it complicated by using pointers. always look for the easiest slickest solution possible. if you want to learn about pointers create a data structure, let's said a double link list, and play with it, that'll teach you. also decide whether you want to do it in c or c++, there are related but very different at the same time.

---

### Post by Some Penguin on 2009-12-18
From the phrasing, it sounds like an assignment where he specifically was instructed to use pointers.

Re: changing the bytes pointed to (well, those and the following bytes)  -- of course, one should be careful about bounds-checking when the strings are of different lengths.  realloc() may work, but in such a case success cannot be guaranteed since there may simply not be enough unallocated virtual address space following the shorter string for it to reallocate in the same address.

---

### Post by Arndt on 2009-12-18
> **Some Penguin said:**
> From the phrasing, it sounds like an assignment where he specifically was instructed to use pointers.

Re: changing the bytes pointed to (well, those and the following bytes)  -- of course, one should be careful about bounds-checking when the strings are of different lengths.  realloc() may work, but in such a case success cannot be guaranteed since there may simply not be enough unallocated virtual address space following the shorter string for it to reallocate in the same address.

The bytes pointed to are probably in read-only memory, and that's probably why the first version got a segmentation fault.

---

### Post by Some Penguin on 2009-12-18
No.  Those weren't const; the compiler has no business putting those strings in read-only memory.  It segfaulted because he doesn't understand pointers[FONT=monospace] and dereferencing.   *temp = <bleah> is going to explode with high frequency if 'temp' is an uninitialized pointer.  At *best*, it segfaults; at worst, it writes that <bleah> into some valid but unexpected address which can conceivably cause very subtle and hard-to-debug issues later.
[/FONT]

---

### Post by dwhitney67 on 2009-12-18
> **OVERPOWER8 said:**
> 
Program must be with pointers and with one extra function:

Why must pointers be used?  Is this homework??

---

### Post by Arndt on 2009-12-19
> **Some Penguin said:**
> No.  Those weren't const; the compiler has no business putting those strings in read-only memory.  It segfaulted because he doesn't understand pointers[FONT=monospace] and dereferencing.   *temp = <bleah> is going to explode with high frequency if 'temp' is an uninitialized pointer.  At *best*, it segfaults; at worst, it writes that <bleah> into some valid but unexpected address which can conceivably cause very subtle and hard-to-debug issues later.
[/FONT]

You may think so, but I invite you to try this program (with C or C++):

```
int main()
{
    char* Name1 = "Winona";

    *Name1 = 'B';
}

```

String constants are 'const', unless some particular option is given to the compiler. Whether the standard(s) say they must be, or if this is at the compiler's discretion, I don't know.

---

### Post by Some Penguin on 2009-12-19
Sure.  It may or may not work, depending on the compiler and the options.  For instance, prior to gcc-4.0, -fwritable-strings enabled precisely what it you would think it did -- 

The best solution to these problems is to change the program to use char-array variables with initialization strings for these purposes instead of string constants.  But if this is not possible, you can use the `-fwritable-strings' flag, which directs GCC to handle string constants the same way most C compilers do. `-traditional' also has this effect, among others.
-- [http://www.delorie.com/gnu/docs/gcc/gcc_121.html](http://www.delorie.com/gnu/docs/gcc/gcc_121.html)

It's not good practice because it IS compiler dependent and therefore unreliable in a heterogeneous environment.  What isn't uncertain at all is that the original poster's original program was attempting to write to an address specified by an uninitialized pointer before it even attempted to modify strings which may or may not be writable depending on the compiler and options used.

---

### Post by LKjell on 2009-12-19
Even if the strings are not constant swapping their content is a no no since they have different size.

---

### Post by Arndt on 2009-12-19
> **Some Penguin said:**
>  What isn't uncertain at all is that the original poster's original program was attempting to write to an address specified by an uninitialized pointer before it even attempted to modify strings 

Yes, you're right there.

---

