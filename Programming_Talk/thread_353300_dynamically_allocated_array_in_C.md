---
title: "dynamically allocated array in C"
date: 2007-02-04
forum: Programming Talk
---

### Post by nitro_n2o on 2007-02-04
Hi all, 
I have a question about malloc'd arrays in C.... 
How can i copy the content from one malloc'd array to another bigger malloc'd array??

Thx in advanced

---

### Post by duff on 2007-02-04
memcpy

---

### Post by Lux Perpetua on 2007-02-04
> **nitro_n2o said:**
> Hi all, 
I have a question about malloc'd arrays in C.... 
How can i copy the content from one malloc'd array to another bigger malloc'd array??

Thx in advancedAlso, you should be aware of realloc, which allows you to allocate a larger array and move your old array to it in one step. (You can also shrink your array if that's what you want to do.)

---

### Post by nitro_n2o on 2007-02-04
hey duff, thx for the reply
but still i get the same error..... 
i'm doing something like this 

```
void grow(char **newArray, char **oldArray, int *capacity) {
    int newCapacity = *capacity * GROWTH_FACTOR * sizeof(char*)
    *newArray = (char**)malloc(newCapacity);
     if(newArray = NULL) {.....}
     
     memcpy(*newArray, oldArray, *capacity);
     capacity = &newCapacity;
}
```

Can somebody tell me why it's wrong

Thx

---

### Post by nitro_n2o on 2007-02-04
no i don't wanna shrink it for now, i'll be super happy if i can grow it :)

---

### Post by lazka on 2007-02-04
just wondering.. whats wrong with realloc?

---

### Post by nitro_n2o on 2007-02-04
i don't know what wrong with realloc :D i'm a totally n00b... 
ok how can i do this without any memory stuff 

if it was java 

i would say 

String[] a = new String[a.length*2];
for(int i=0; i<a.length; i++)
   a[i] = old[i];

old = a;


how can i do this in C :(  i'm totally puzzled

---

### Post by LordHunter317 on 2007-02-04
> **nitro_n2o said:**
> hey duff, thx for the reply
but still i get the same error..... 
i'm doing something like this 

```
void grow(char **newArray, char **oldArray, int *capacity) {
    int newCapacity = *capacity * GROWTH_FACTOR * sizeof(char*)
    *newArray = (char**)malloc(newCapacity);
     if(newArray = NULL) {.....}
     
     memcpy(*newArray, oldArray, *capacity);
     capacity = &newCapacity;
}
```

[quote=nitro_n2o]Can somebody tell me why it's wrongYes:[list][*]Why the hell are you passing capacity as a pointer.  That doesn't make any sense whatsoever.  Capacity is a constant in this operation, assuming GROWTH_FACTOR is a constant.  Unless you're not exporting that to the public (which you damn well should be) there's no reason for the senseless complication. [*]Your sizeof() is wrong, assuming you're trying to enlarge the  buffer to hold a string.  char* and char are distinct types.  You don't need sizeof(char) ever, because sizeof(char) == 1 always.  If you're really trying to reallocate an array of char*, then you need to pass char***.[*]Never ever typecast malloc in C.  It can hide errors.  Including the one you made[*]Your arguments to memcpy are incorrect.  Here's a hint: if the source and dest are different types, you're likely doing something super-dangerous.[/list]You really should use realloc().  In fact, I would use realloc() unless you have a reason not to.  And you don't have a reason until you've read the C-FAQ on pointers.

---

### Post by LordHunter317 on 2007-02-04
From your Java example, I'm not sure what you're trying to do.  Are you trying to copy an array of strings into a larger array, or a string into a larger array?  The massive type errors make it impossible to discern intent.

---

### Post by nitro_n2o on 2007-02-04
it seems that i didn't explain my point well, sorry for that 

i have a program and a 2d array is the main structure char** and i'm inserting stuff into it.. now when the array gets full i wanna malloc a new array double the size of the old one and copy all pointers to it. 

then the capacity should change to the new capacity and i should free the old array.... 

i'm really a n00b i still now nothing in C 

:( :(

---

### Post by LordHunter317 on 2007-02-04
No, just use realloc.  You don't want to copy that.  It's a pain.  realloc works right in all situations, when used correctly.

But you need to post the code to allocate it.  Behavior with a linearly contiguous 2D array is different from array-of-char*s, where each row isn't contiguous in memory.

---

### Post by nitro_n2o on 2007-02-04
i can't use realloc :(  that would be so easy... if i'm still not good in C that doesn't mean i should give up..... 
guys come on you should be C gods.. .You are Ubuntu ppl :) give me some nice bright idea, it's getting late i need a shower so badly :(

---

### Post by nitro_n2o on 2007-02-04
or at least can somebody tell me what is *** glibc detected *** if had enough of Segmentation Fault for today, and know i'm seeing new crazy things

---

### Post by LordHunter317 on 2007-02-04
> **nitro_n2o said:**
> i can't use realloc :( Why not?

> You are Ubuntu ppl :) give me some nice bright idea, it's getting late i need a shower so badly :(You won't give us what we ask for, so we cannot.  **Go read the C FAQ**.

---

### Post by nitro_n2o on 2007-02-04
i tried realloc it doesn't work 

i have a method to loadArray(***array, *capacity, char[] word) 

and to realloc i used this 

realloc(*array, 2 * (*capacity*sizeof(char *)));


it  gives me Segmentation Fault

---

### Post by LordHunter317 on 2007-02-04
**Single lines will not help.  We need entire blocks of code.**

That line is wrong.  You're not assigning, so it's wrong.  And if you have an array of char* instead of a contiguous array, you have to do a deep copy.  If you have a contiguous array you do not,  but you *must* properly allocate the entire 2D space.  You're not currently doing that, AFAICT.

---

### Post by nitro_n2o on 2007-02-04
That's how i'm loading data into the array 
*count is a pointer to current number of elements, it will incremented by insert 
*capacity is a pointer to the max capacity for the array 

[

---

### Post by LordHunter317 on 2007-02-04
Ok, several things:[list][*]I would use a linked list of fixed size buffers to read data in, then concatonate them together into one big buffer at the end, if you're going to that route.  But you don't have to, see a few points down.[*]Unless you must return error values through int (you probably don't need to), don't pass capacity as a pointer.    You can almost certainly return -1 on error and capacity otherwise[*]You almost certainly don't want to use the value of capacity for the first allocation.[*]You can almost certainly count both: the number of words in the file, the number of bytes per word and preallocate the arrays correctly, saving the need for reallocation ever.  This prevents you from using a stream input, but if you know it will be a file from disk it's not an issue.[*]Every bullet from above still applies.[*]fscanf is not safe, don't use it.[*]Count certainly sohuldn't be passed in, so don't.  It shouldn't be a pointer, either.[*]You neve allocate space to store the actual words, just pointers to the words.  For every word you wish to read, you need to do a malloc(// however big the word is) and take the char* returned by that and store it in array.  Then, store the word there.[/list]An explanation of what this code is trying to do overall would be helpful.

---

### Post by nitro_n2o on 2007-02-04
i know that my code is vulnerable to Buffer Overflow attack but i don't know other ways to do that.... However, 
in main i declare 
```
char **wordArray;
int capacity = INITIAL_MAX;
int wordCount = 0;

```
then i do some stuff not important, after that i do: 
 ```
loadArray(argv[1], &wordArray, &wordCount, &capacity )
```

argv[1] is the name of input file... then code in loadArray should read data from file, allocate the necessary space for it, and calls method insert (which works perfectly), to insert this word into my array (*array) => **wordArray (the array allocated at main)

but if data gets large i'll need to grow the array, to do this i wanted to have a function that mallocs a new array double the size of the old one, copy all pointers from the old array to the new one, and change capacity accordingly.. so i continue with insertion with no problems 

and that is the part i'm stuck in...the new big array allocation...

---

### Post by LordHunter317 on 2007-02-04
> **nitro_n2o said:**
> i know that my code is vulnerable to Buffer Overflow attack but i don't know other ways to do that....Then you need to learn.  The best way would be to fill a fixed size buffer (say, 1024 bytes) and then fetch the words out of that. 

> and that is the part i'm stuck in...the new big array allocation...No, that's just it.  **All** of your code is wrong, both in implementation and design.  Go read the C FAQ, which covers a lot of these topics, at least briefly.

If I'm feeling particularly nice I'll post an example of loading words from a file soon.

---

