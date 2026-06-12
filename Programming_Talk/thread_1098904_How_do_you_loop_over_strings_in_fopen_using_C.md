---
title: "How do you loop over strings in fopen using C?"
date: 2009-03-17
forum: Programming Talk
---

### Post by jsmidt on 2009-03-17
I have a code written in C which looks like this

```

        FILE *file[N];

        file[0] = fopen("myfile_1", "r");
        file[1] = fopen("myfile_2", "r");
        file[2] = fopen("myfile_3", "r");
        file[3] = fopen("myfile_4", "r");
        file[4] = fopen("myfile_5", "r");

```

How do I write this in C with a loop which looks something to the effect:

```
for (i = 0; i < N; i++)
       file[i] = fopen("myfile_"+(i+1));
```

So I can change N as I wish?  The problem is I can't loop over strings like that.  Does anybody know how this can be done in C?

---

### Post by albandy on 2009-03-17
edited: my error, what I said don't work
but I remember the existence of malloc function, it let you create dynamic memory allocation. search for malloc and dynamic arrays.

Also if were java a simply new will work

---

### Post by cb951303 on 2009-03-17
something like this should work.
```

    for (i = 0; i < N; i++)
    {
           char myfile[16];
           sprintf(myfile, "myfile_%d", i);
           file[i] = fopen(myfile, "r");
    }

```

---

### Post by jsmidt on 2009-03-17
Thanks a lot.

---

### Post by Habbit on 2009-03-17
Actually, in order to avoid possible [_buffer overflows_]("http://en.wikipedia.org/wiki/Buffer_overflow"), you should use the "safe" versions of the well-known C library functions from C99, which allow you to specify the size of the buffer you are writing to. In this case it does not matter because you statically know the file name size and the maximum width of a number you'd append, but in many real-world applications, using **snprintf** instead of sprintf will prevent nasty bugs that can compromise security and/or data integrity, not to mention cause a crash.

```

#define BUFLEN 16
    for (i = 0; i < N; i++)
    {
           char myfile[BUFLEN];
           int requiredChars = snprintf(myfile, BUFLEN, "myfile_%d", i);
           assert(requiredChars < BUFLEN);
           file[i] = fopen(myfile, "r");
    }
```Of course, a test that did not kill the program if a 16-char file name was generated would be nicer, but the action to take in that case depends on you.

---

### Post by slavik on 2009-03-17
> **Habbit said:**
> Actually, in order to avoid possible [_buffer overflows_]("http://en.wikipedia.org/wiki/Buffer_overflow"), you should use the "safe" versions of the well-known C library functions from C99, which allow you to specify the size of the buffer you are writing to. In this case it does not matter because you statically know the file name size and the maximum width of a number you'd append, but in many real-world applications, using **snprintf** instead of sprintf will prevent nasty bugs that can compromise security and/or data integrity, not to mention cause a crash.

```

#define BUFLEN 16
    for (i = 0; i < N; i++)
    {
           char myfile[BUFLEN];
           int requiredChars = snprintf(myfile, BUFLEN, "myfile_%d", i);
           assert(requiredChars < BUFLEN);
           file[i] = fopen(myfile, "r");
    }
```Of course, a test that did not kill the program if a 16-char file name was generated would be nicer, but the action to take in that case depends on you.
when a buffer is overflowed ... the BEST thing is that the code crashes ;)

---

### Post by Krupski on 2009-03-18
> **Habbit said:**
> Actually, in order to avoid possible [_buffer overflows_]("http://en.wikipedia.org/wiki/Buffer_overflow"), you should use the "safe" versions of the well-known C library functions from C99, which allow you to specify the size of the buffer you are writing to. In this case it does not matter because you statically know the file name size and the maximum width of a number you'd append, but in many real-world applications, using **snprintf** instead of sprintf will prevent nasty bugs that can compromise security and/or data integrity, not to mention cause a crash.

```

#define BUFLEN 16
    for (i = 0; i < N; i++)
    {
           char myfile[BUFLEN];
           int requiredChars = snprintf(myfile, BUFLEN, "myfile_%d", i);
           assert(requiredChars < BUFLEN);
           file[i] = fopen(myfile, "r");
    }
```Of course, a test that did not kill the program if a 16-char file name was generated would be nicer, but the action to take in that case depends on you.

I asked this before in another thread and didn't get an answer...

I wonder... how can "sprintf" be unsafe if the buffer is much larger than the result could ever be?

Does the prototype string get modified in place before it's copied, or is it "picked apart" and copied on the fly?

In other words, does THIS happen:

```

    i = 10000;
    sprintf(myfile, "myfile_%d", i);
    strcpy(myflle, "myfile_10000");

```

...or does this happen:

```

    i = 10000;
    sprintf(myfile, "myfile_%d", i);
    strcpy(myfile, "myfile_");
    strcat(myfile, "10000");

```

The point I'm (trying) to make is... is a static string (dangerously) arbitrarily enlarged in memory, or is the destination buffer built up out of pieces?

I'm not seeing how "sprintf" is dangerous...

Thanks!

-- Roger

---

### Post by Habbit on 2009-03-18
> **slavik said:**
> when a buffer is overflowed ... the BEST thing is that the code crashes ;)
Maybe, but in a rational, controlled manner, which is just what my code would do: it would assert on that exact point and you would be able to go to that source file and say "Oh! So that buffer overflowed". If you do it the "traditional" way, sprintf will actually clobber data past the end of the buffer since it has no way to know where the end is. Since the buffer in the example was stack-allocated, sprintf could have clobbered other local variables, the return PC, function arguments and basically anything over its position in the activation frame for the function.

---

### Post by Habbit on 2009-03-18
> **Krupski said:**
> I asked this before in another thread and didn't get an answer...

I wonder... how can "sprintf" be unsafe if the buffer is much larger than the result could ever be?

Does the prototype string get modified in place before it's copied, or is it "picked apart" and copied on the fly?

In other words, does THIS happen:

```

    i = 10000;
    sprintf(myfile, "myfile_%d", i);
    strcpy(myflle, "myfile_10000");

```

...or does this happen:

```

    i = 10000;
    sprintf(myfile, "myfile_%d", i);
    strcpy(myfile, "myfile_");
    strcat(myfile, "10000");

```

The point I'm (trying) to make is... is a static string (dangerously) arbitrarily enlarged in memory, or is the destination buffer built up out of pieces?

I'm not seeing how "sprintf" is dangerous...

Thanks!

-- Roger

The problem is not your "prototype string", but your destination buffer. In both of your examples (assuming that buffer was small enough, say, 10 bytes), the full "myfile_10000\0" string (13 bytes long) would be written to memory without taking into account that "buffer" is only 10 bytes long. First, those functions you write do not know the buffer length, and second, even if they did, they will not try to realloc your buffer to be bigger (since that could fail and/or invalidate other pointers to a place they do not own). Thus, anything (local variables, the function return address, etc) in the 3 bytes after the buffer would be overwritten with '0', '0', '\0'. This is the main way stack buffer overflow attacks are crafted, and using snprintf allows you to at the very very least avoid them and do something when the buffer is too small (either allocate a bigger buffer, complain to the user or just assert and die, but without causing additional trouble).

---

