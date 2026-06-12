---
title: "POSSIBLE?? dynamically allocate memory for a string set to the size of that string?"
date: 2008-02-28
forum: Programming Talk
---

### Post by S15_88 on 2008-02-28
Sorry if the topic was a little vague.  What i'm trying to fgure out is:

is it possible to malloc() memory for a char pointer as the string is being read in so that it allocates memory for the exact size of the string?

An example is i had to make a program for school that went through a text file and scanned in one word at a time and calculated the amount of syllables, added +1 to the word count, and every time it hit an end of sentence marker(.?!) sentences +1.  

what the prof did was make a text file that had no spaces so we were forced to seperate words, we were given the text file so i knew how big the string had to be.  but what if i didn't know the maximum length of the string?  

I have no clue as to how this would be possible...any ideas?

if you want i can post my code, it's already been marked i got 95% on it so i was happy but i'm just curious as to whether this is possible.
Thanks, Alain

---

### Post by Wybiral on 2008-02-28
It's probably null-terminated, meaning there's a character '\0' denoting the end of the string (in which case you can use [strlen]("http://cppreference.com/stdstring/strlen.html")). But if it's a file, then you can get the file size by [fseek]("http://cppreference.com/stdio/fseek.html")ing to the end, getting the file position with [ftell]("http://cppreference.com/stdio/ftell.html") (then allocating a buffer with that size + 1 for the null terminator), and returning to the beginning to [fread]("http://cppreference.com/stdio/fread.html") the string.

---

### Post by S15_88 on 2008-02-28
if the input is coming from stdin, wouldn't you have to store the string then do the strlen...therefore you would have to originally statically allocate space for the string before you could do the strlen().   

i'm just puzzled as to how to get the length then allocate the memory! gahhh! haha

Thanks, Alain

---

### Post by winch on 2008-02-28
[realloc]("http://www.gnu.org/software/libtool/manual/libc/Changing-Block-Size.html")  allows you to increase the size of a block of memory allocated by malloc.

So you can malloc a small buffer. Then every time you fill it use realloc to make it bigger.

---

### Post by stroyan on 2008-02-28
If you use scanf rather than read you can pass a format string that tells scanf to malloc memory for a string.
Here is an example using "a" to allocate and "*" to suppress returning the delimiters.

[PHP]#include <malloc.h>
#include <stdio.h>

int main(int argc, char *argv[])
{
    int res;
    char *w;

    while (1 == (res = scanf("%a[^ \n\t,]%*[ \n\t,]", &w))) {
        printf("'%s'\n", w);
        free(w);
    }
    return 0;
}[/PHP]

---

### Post by k2t0f12d on 2008-02-29
> **S15_88 said:**
> is it possible to malloc() memory for a char pointer as the string is being read in so that it allocates memory for the exact size of the string?

I actually tackled this exact idea in a program I was writing in C purely for the reason of seeing if I could do it.  Since the programmer cannot guess the length of the input string *before* it is actually typed, my solution was to create a buffer array large enough to hold any reasonable input, read its length, allocate that much memory, and then copy the buffer into the newly acquired memory.

It's probably not very practical except purely for exercise of trying to do it.  Eventually at some point you are going to waste memory anyway.  In my program, it was wasted in the padding of the buffer.  A linked list would solve this problem pretty well, at least to avoid padding, since you could allocate each character and store it atomically, copy its final contents to a dynamically allocated array, then free the list.

---

### Post by Lux Perpetua on 2008-02-29
winch's solution is pretty robust. Allocate a small buffer (not a horrendously large one). You will eventually fill it; every time you do, double its size. Since you double its size every time you reallocate, you are guaranteed not to do too many reallocations, and your buffer is never more than twice as big as it needs to be. You can even shrink the array at the end to reclaim the unused padding at the end. This is the way STL vectors work in C++ (except the reclaiming part).

---

