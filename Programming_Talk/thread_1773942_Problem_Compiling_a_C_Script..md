---
title: "Problem Compiling a C Script."
date: 2011-06-02
forum: Programming Talk
---

### Post by gdodge77 on 2011-06-02
Hello,
I'm working on a research project with a group at RIT, and we need to use a script to pull data from .xml files and export them as another type. 

The script is already written and was used in the past but I cannot for the life of me get it to compile. 

I've attached a .zip containing the .c and .h files that I have been using. 

I'm attempting to compile the .c file by using:
gcc -c jessconvert.c

The error that I am receiving is also attached.

---

### Post by Vaphell on 2011-06-02
According to [http://linux.die.net/man/3/strstr](http://linux.die.net/man/3/strstr) you need to include this line ```
#define _GNU_SOURCE
``` in your .h to have that int-to-pointer cast warnings related to strcasestr() go away.

besides why C? Was it worth the hassle of playing with pointers?

---

### Post by gdodge77 on 2011-06-02
Well I really am an absolute noob when it comes to using C. I've dabbled in python, but thats about it.

I was basically handed this script and told make it work by my research advisor.

---

### Post by gdodge77 on 2011-06-02
Great! the strcaster error is gone now. The errors in 'dumpatom' appear to be some sort of syntax thing.

---

### Post by Vaphell on 2011-06-02
do you have CVector? CVector.h is mentioned in .h and all these errors are related to CVectorSomething

---

### Post by gdodge77 on 2011-06-02
Yeah CVector is installed and working.

---

### Post by alexmurray on 2011-06-03
These aren't errors - they're only warnings so whats the issue? If you really care the following should do the trick:

As mentioned above defining __GNU_SOURCE will fix the strcasestr warnings
If you add the line
```

int findtemp(const char * pattern, size_t * temploc;

```
to declare the findtemp function at say line 43 that will remove the warnings for that.

Adding the #include <stdlib.h> at the top will remove the atoi warnings

The format not a string literal warnings can be fixed by replacing those two lines:
```

        fprintf(stdout,curop);

```

with
```

        fprintf(stdout,"%s", curop);

```

And for the CVectorElementAt warning just make sure CVector.h is in the include path - ie. under /usr/include

But as I said at the start these are not errors, simply warnings - it has compiled fine - for completeness you should address them all but it won't effect the final result.

---

### Post by gdodge77 on 2011-06-03
Thanks a lot alex.

Just goes to show how out of my element I am... ](*,)

Guess that's what I get for being a biochemist!

If anyone is interested in the work that we're actually doing you can check it out at [http://sbevsl.sourceforge.net/](http://sbevsl.sourceforge.net/)

---

### Post by gdodge77 on 2011-06-03
OK, new problem. I guess I didn't install CVector and mxml to the correct directories. What should the default location for these files be to make sure that they are correctly recognized in my path?

---

### Post by Petrolea on 2011-06-04
> **gdodge77 said:**
> OK, new problem. I guess I didn't install CVector and mxml to the correct directories. What should the default location for these files be to make sure that they are correctly recognized in my path?

Usually /usr

---

