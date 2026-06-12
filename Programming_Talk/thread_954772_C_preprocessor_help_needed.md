---
title: "C preprocessor help needed"
date: 2008-10-21
forum: Programming Talk
---

### Post by billvb on 2008-10-21
Hello Everyone,

I'm beginning development of a modestly sized application in C using eclipse.  I've come to a situation where i've never had to use the C preprocessor in such a way before:

This is (sort of) what the heirarchy looks like (+ denote folders, - denote files):
```

+ src
 + crypto
   - crypto.h
   + DES
     - DES.c
   + 3DES
     - 3DES.c
 + others...

```

crypto.h will have two prototypes, lets say encrypt(..) and decrypt(..).

Since this project will be for an embedded application, I was the encryption algorithm to be known at compile time (e.g., DES, 3DES, etc..) and I want to accomplish this by using preprocessor #defines and #includes.

i.e.,
```

#define DES
/* #define AES */

#ifdef DES
  (use definitions from ./DES/des.c)
#elif 3DES
  (use definitions from ./3DES/3des.c)
#elif AES
  (use def from ./AES/aes.c)
#else
  (throw error or something)
#endif


/* each of the specific crypto files will contain
definitions of these, note: this is temporary, they
won't really be doing operations just on ints */
int encrypt(int);
int decrypt(int);

```

The whole point is so that lower level details are completely hidden from higher level source files.  The specific question I'm asking is that
1: is the control structure I listed above appropriate
and 2: would each of the crypto c files require their own headers?

Thanks so much.

---

### Post by snova on 2008-10-21
Unless you had a reason for doing it this way, I have another idea. Don't bother with separate headers! If all of your algorithms support the same interface, then modify the build system so that it only links one file. One header fits all. No preprocessor necessary.

---

### Post by rnodal on 2008-10-22
Have you tried inserting an include statement in between the:
```
#ifdef DES
  (use definitions from ./DES/des.c)
#elif 3DES
  (use definitions from ./3DES/3des.c)
#elif AES
  (use def from ./AES/aes.c)
#else
  (throw error or something)
#endif


```
?

-r

---

### Post by dwhitney67 on 2008-10-22
For distinctions at compile time, rely on the Makefile.

When you run "make", specify which algorithm you want employed.
```

SRCS = file1.c

ifeq (${ALG}, DES)
    SRCS += fileDES.c

else ifeq (${ALG}, 3DES)
    SRCS += file3DES.c

else
    SRCS += fileAES.c
endif

```

For example:
```
make ALG=3DES
```

With respect to a header file to define the interface of a particular encryption algorithm, go with Snova's remarks.  All you should need is one header file that defines the input/output of a encryption/decryption function, if not a wrapper-function to the lower-level function.

---

