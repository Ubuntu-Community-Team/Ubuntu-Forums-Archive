---
title: "Need a little help please..."
date: 2010-02-28
forum: Programming Talk
---

### Post by Krupski on 2010-02-28
Hi all,

(first of all, disclaimer: I am not a student and this is not homework - this is a personal project)

OK, now I have a "clone" of the function "basename" that I wrote so I could also compile the code in Windows if I wanted to.

Here's the function (it works just fine):

```

// destination, source, delimiter
int bname(char* str, const char* p0, const char* delim)
{
    char tmp[BUFSIZ];
    char* p1;
    char* p2;

    // make a local copy of the input string
    strncpy(tmp, p0, BUFSIZ);

    p2 = strtok(tmp, delim);

    while(p2 != NULL) {
        p1 = p2;
        p2 = strtok(NULL, delim);
    }

    // copy the tail to the caller's buffer
    strncpy(str, p1, BUFSIZ);

    return strlen(str);
}

```

The input parameters are DESTINATION BUFFER, SOURCE STRING, DELIMITER STRING.

If the input source string is "/usr/bin/program", and the delimiter is "/", the buffer is filled with "program".

What I need is the REVERSE of this code (and I don't want to use "DIRNAME"... I want a companion function like above).

In other words, I also want to be able to get the "/usr/bin/" part of the string.

I tried to do it myself but it's just not clicking. Maybe I'm tired, but it's going nowhere and I'm at my wit's end.

I'm sure what I need is a minor modification to what I already have, but for the life of my I just can't get it.

Any help will be GREATLY appreciated.

Thanks!

-- Roger

---

### Post by gmargo on 2010-02-28
Just use strrchr(3) to find the last slash.  No need for strtok(3).

```

char * slash = strrchr(p0, delim);

/* Basename: */
strcpy(str, slash+1);

/* Dirname: */
strncpy(str, p0, slash-p0);
str[slash-p0] = '\0';

```

---

### Post by Krupski on 2010-02-28
> **gmargo said:**
> Just use strrchr(3) to find the last slash.  No need for strtok(3).

```

char * slash = strrchr(p0, delim);

/* Basename: */
strcpy(str, slash+1);

/* Dirname: */
strncpy(str, p0, slash-p0);
str[slash-p0] = '\0';

```

WOW!!!!!!!!!!!

Thanks a 1e6!  :)

Thank you!!!

-- Roger

(edit to add): I modified it slightly so that I could still use STRTOK (which accepts multiple delimiter characters) while still using your idea of copying only the proper number of bytes as determined by pointer arithmetic.

Here's the result:

```

// basename - destination, source, delimiter
int bname(char* str, const char* p0, const char* delim)
{
    char tmp[BUFSIZ];
    char* p1;
    char* p2;

    if(strlen(p0) != 0) {
        strncpy(tmp, p0, BUFSIZ);

        p2 = strtok(tmp, delim);

        while(p2 != NULL) {
            p1 = p2;
            p2 = strtok(NULL, delim);
        }
        strncpy(str, p1, BUFSIZ);
    }
    return strlen(str);
}

```


```

// dirname - destination, source, delimiter
int dname(char* str, const char* p0, const char* delim)
{
    char tmp[BUFSIZ];
    char* p1;
    char* p2;

    if(strlen(p0) != 0) {
        strncpy(tmp, p0, BUFSIZ);

        p2 = strtok(tmp, delim);

        while(p2 != NULL) {
            p1 = p2;
            p2 = strtok(NULL, delim);
        }
        strncpy(str, p0, strlen(p0)-strlen(p1));
    }
    return strlen(str);
}

```


Again, thank you so much for the help!

-- Roger

---

### Post by Tony Flury on 2010-03-01
Just as an aside - you are dependent on the caller of your functions providing a buffer that is big enough (i.e. so that the strcpy) works.

for complete flexibility and safety, you should pass the size of the destination buffer str as an argument, and check to ensure that you don't try to copy over that size.

I know that only you will call your function, but it is a good habit to get in to, and it is those sort of good habits that will save pain on larger projects.

Also what happens if the path is larger than your BUFSIZE - the first strncpy will end up without a null termination - which is not a good thing as your eventual output string will end up without the null termination as well.

---

### Post by Krupski on 2010-03-03
> **Tony Flury said:**
> Just as an aside - you are dependent on the caller of your functions providing a buffer that is big enough (i.e. so that the strcpy) works.

for complete flexibility and safety, you should pass the size of the destination buffer str as an argument, and check to ensure that you don't try to copy over that size.

I know that only you will call your function, but it is a good habit to get in to, and it is those sort of good habits that will save pain on larger projects.

Also what happens if the path is larger than your BUFSIZE - the first strncpy will end up without a null termination - which is not a good thing as your eventual output string will end up without the null termination as well.


I have a question about MALLOC()... if I allocate a block of memory, do I *HAVE* to free it with FREE() or can I use REALLOC() with a size of zero?

For example, I know how to do this:

```

buffer = (char*)malloc(8192);
...use buffer...
free(buffer);

```

But can I do THIS:

```

buffer = (char*)malloc(8192);
...use buffer...
realloc(buffer, 0);

```

My concern is, if for some reason I have to resize the initial "buffer", will free() return ALL of the allocated memory? How does it know how much in total to return?

If I just re-allocate it to a size of 0, isn't that the same thing?

Sorry for the newbie questions... but I'm learning slowly but surely (mostly slowly!) :)

Thanks!

-- Roger

---

### Post by Some Penguin on 2010-03-04
> **Krupski said:**
> 
If I just re-allocate it to a size of 0, isn't that the same thing?


Have you read the realloc() man page?

---

### Post by Krupski on 2010-03-04
> **Some Penguin said:**
> Have you read the realloc() man page?

Yes I have... and from what I read it *seems* like I can indeed release memory by re-allocating with a size of zero... my question was really "does it work" and "is it OK" and "should I do it the proper way (i.e. free())"?

I ask because lots of times people tell me "what you're doing works, but it's the wrong way to do it" and I want to do it the RIGHT way.

Also, if I allocate a memory block with malloc(), I get a return value of "pointer to memory" or NULL (if it failed), but I don't know how to get the SIZE of the block allocated.

The documentation says "the requested size is rounded up to the proper number of header sized units" (page 186, "The C Programming Language, Second Addition by K&R").

The book also shows a diagram of the returned block... a pointer to the first byte of allocated space and some data (ints maybe?) directly behind the pointer which tells the size of the block and a pointer to the next block.

I tried to find out the actual allocated block size by looking at "pointer-1" and it didn't work.

Is there any way or any function I can call that will tell me the size of the memory block that malloc() actually gave me?

I'm sure right now you're thinking "dummy... the size of the block is the size you asked for!", and I know that... but I want to know is there a way to actually GET the block size with a function call (like I can do a "strlen()" to see how long a string is)?

Thank you!

-- Roger

---

### Post by MadCow108 on 2010-03-04
you can't with glibc's malloc in release mode (to my knowledge at least).
The allocator may have size information internally, but you are not allowed to mess with that.
Even if, it would be highly non-portable.

The reason strlen can do that is that strings have a termination in form of a null byte and no string character is coded to a null byte.
This last requirement for this technique does not work when the block may contain arbitrary data (like with malloc) and so no special end of block marking is possible.

Also strlen is slow. it must scan the entire string to find the length. I can't think of any reason why you would want to do that with malloc'd memory (except debugging)

You could of course write an allocator which saves the size along with the pointer to the block in some management structure and returns that instead of the memory pointer directly.
But use of that would be rather limited in productive code although memory debuggers probably do such kind of stuff to check for buffer overflows.

---

### Post by Krupski on 2010-03-04
> **MadCow108 said:**
> you can't with glibc's malloc in release mode (to my knowledge at least).
The allocator may have size information internally, but you are not allowed to mess with that.
Even if, it would be highly non-portable.


Well... here's where my confusion sets in.

Several posts up, it was suggested to me that when I write a program with buffer(s), the buffers should be allocated rather than compiled to a fixed size.

I WAS simply declaring them with a large number (like 8192) so that they would always be larger than I'd ever need.

But, the idea of allocating as needed sounded nicer.

When I got into trying it, my thought was to do something like this (pseudo-code):

```

char* buffer = malloc(start_small);
while(size_of_buffer < incoming) {
    realloc(buffer, size_of_buffer + increment);
}
read_incoming();

```

But to do that, I need to know the size of the allocated buffer!

I could have a separate INT which has the buffer size and is used as a variable in malloc() and realloc(), but that seems awkward.

In the end, I got the gut feeling that I was going about it all the wrong way... but I can't seem to figure out the RIGHT way to do it (and simply allocating a larger-than-necessary static size doesn't seem all that bad anyway... given that it's relinquished when the program ends).

So, should I be perusing the "malloc method" or isn't it worth it?

-- Roger

---

### Post by Tony Flury on 2010-03-04
the "right" way of doing dynamic memory allocation is to keep track of the memory you have allocated, if you are going to realloc if you are close to overflowing that buffer.

The main danger of having a function which allocates a buffer, is that the caller has to know that the function used malloc to create the buffer, and the calling level needs to then free it when it is ready - if you don't you will have a memory leak.

If you want to keep all the control at the same level - then you should have the caller allocate and free its own memory, and pass its own buffer, and critically the length, to your function - and your function should honour the buffer length it is told.

---

### Post by Krupski on 2010-03-04
> **Tony Flury said:**
> If you want to keep all the control at the same level ......... and your function should honour the buffer length it is told.

I did that in a roundabout way by (re)defining "BUFSIZ" and then using THAT exclusively (when declaring variables, doing strncpy, doing reads, etc...). I thought that if I used the same number for everything, I would never overrun a buffer.

I know it's wasteful... for example... to reserve an 8192 byte buffer for a 16 byte filename, but I accepted the waste so that everything else would be large enough (and I wouldn't have to worry about allocating, reallocating and freeing memory or worse... a memory leak).

The whole point of my "text to html" filter program is to run it inside a little BASH script, run it say, every 5 seconds and copy various system info to an HTML file that I can view remotely.

Since it would run every 5 seconds for days, weeks or more on end, obviously a memory leak would turn into a disaster.

Do you think malloc() is even used very much anymore? Being able to allocate an *exact* amount of memory seems more like what someone 25 years ago would do when KILObytes were scarce.

Today with gigabytes available, should I really care about saving a few KBytes by using malloc()?

Thanks again for your replies and your attention to my questions!

-- Roger

---

