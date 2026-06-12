---
title: "Compile time error with struct"
date: 2010-12-22
forum: Programming Talk
---

### Post by Tcressy on 2010-12-22
This is probably a simple fix, but I have been searching forums/google unable to find a work around. Here is what I have

> 
#include <stdio.h>
#include <dirent.h>
#include <sys/stat.h>
#include <stdlib.h>

void testFunction(const char *path){
    struct dirent *theList; //=get_list(path);
    int i=0;
    while(NULL != *(theList+i) /*same as theList[i]*/){       
             // some code
             // i++;
    }
}So my compile time error is: error: invalid operands to binary != (have &#8216;void *&#8217; and &#8216;struct dirent&#8217;)

Im affluent in C, arrays, and structs, but i guess not in the combination of the structs and arrays. I understand the error but I dont know how to work around it. Any help is appreciated.

---

### Post by trent.josephsen on 2010-12-22
I guess "affluent in C" means you're awash in expensive books and compilers, but haven't bothered to learn the language.

Look at this line:
```
struct dirent *theList;
```

Now say aloud 100 times, or until it sinks in:  "theList is a pointer to struct dirent."

Now, I have no idea why you would do something like *(theList + i) when theList[i] is available to you, but you can use either one for this next exercise.  Look at this expression:

```
theList[i]
```

What is its type?

Since it is an lvalue and therefore represents an object, how would you go about obtaining a pointer to said object?

Hint:  Does C have an operator for obtaining the address of an object?

Alternatively, is there something you could change in *(theList + i) to make it a pointer and not dereference it?

Hint:  Why is * called the pointer dereferencing operator?

---

### Post by r-senior on 2010-12-22
You can't use == or != on a struct, which is what the ith element of your "array" is. As you have it, I'm guessing you might want this:

```

struct dirent **theList;

```

i.e. a dynamically allocated array (or perhaps a pointer to the head of a linked list) of pointers to struct dirent. Obviously more code needs to be written to allocate and build such an array/list. Or just process the directory entries as you are given them - presumably repeated calls to readdir() come into the plan somewhere?

---

### Post by dwhitney67 on 2010-12-22
> **Tcressy said:**
> This is probably a simple fix, but I have been searching forums/google unable to find a work around. Here is what I have

So my compile time error is: error: invalid operands to binary != (have &#8216;void *&#8217; and &#8216;struct dirent&#8217;)

Im affluent in C, arrays, and structs, but i guess not in the combination of the structs and arrays. I understand the error but I dont know how to work around it. Any help is appreciated.

This is your code, without the dead-code, and contained within CODE tags:
```

#include <dirent.h>

void testFunction(const char *path)
{
   struct dirent *theList;

   int i = 0;

   while (NULL != *(theList+i))
   {
   }
}

```
Now, regardless of what skills you have with C, the code above is quite incomplete... in fact, it is damn close to being useless.

Of course, you have that line above that is causing the compiler to complain.  Fix it!  You have a pointer, and yet are dereferencing it... and then comparing it to NULL.  Where's those C skills you mentioned?

As for "theList", are you ever planning to initialize it to something worthwhile?

---

### Post by Tcressy on 2010-12-23
I should have made this more clear and i apologize...The code isn't important, its just some half assed copy pasta crap i found that produced the error...the point of my post was just to get a simple understanding of the error (I did it on the iphone, lesson learned). The code was just what i used to produce the error. Bad Idea i guess?

---

### Post by dwhitney67 on 2010-12-23
You may want to peruse this [post]("http://ubuntuforums.org/showpost.php?p=10266508&postcount=7") for additional ideas.

---

