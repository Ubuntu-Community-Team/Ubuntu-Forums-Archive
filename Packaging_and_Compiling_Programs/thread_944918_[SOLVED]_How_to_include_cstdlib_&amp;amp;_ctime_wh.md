---
title: "[SOLVED] How to include cstdlib &amp;amp; ctime when compiling a C program with GCC"
date: 2008-10-11
forum: Packaging and Compiling Programs
---

### Post by Samanathon on 2008-10-11
Hi all,

I'm running into a bit of trouble when trying to compile the following with gcc:

```
 1 #include <stdio.h>
 2 
 3 int main()
 4 {
 5    int iRandomNum = 0;
 6    int iResponse = 0;
 7    srand(time());
 8 
 9    iRandomNum = (rand() % 10) + 1;
10 
11    printf("\nGuess a number between 1 and 10: ");
12    scanf("%d", &iResponse);
13 
14    if (iResponse == iRandomNum)
15       printf("\nYou guessed right\n");
16    else {
17       printf("\nSorry, you guessed wrong\n");
18       printf("The correct guess was %d\n", iRandomNum);
19    }
20    return 0;
21 }
```

The program returns the following error when I try to compile: 

```
$ gcc random.c -Wall -g
random.c: In function ‘main’:
random.c:7: warning: implicit declaration of function ‘srand’
random.c:7: warning: implicit declaration of function ‘time’
random.c:9: warning: implicit declaration of function ‘rand’
```

A classmate, who uses some program running in Windows to compile, suggested that I include these libraries:

```
#include <ctime> // For time()
#include <cstdlib> // For srand() and rand()
```

But that returns this error:

```
$ gcc random.c -Wall -g
random.c:2:31: error: ctime: No such file or directory
random.c:3:45: error: cstdlib: No such file or directory
random.c: In function ‘main’:
random.c:9: warning: implicit declaration of function ‘srand’
random.c:9: warning: implicit declaration of function ‘time’
random.c:11: warning: implicit declaration of function ‘rand’

```

Any ideas?!? :confused:

---

### Post by Samanathon on 2008-10-12
Nobody?!

---

### Post by WW on 2008-10-12
> **Samanathon said:**
> 

A classmate, who uses some program running in Windows to compile, suggested that I include these libraries:

```
#include <ctime> // For time()
#include <cstdlib> // For srand() and rand()
```


Those are the C++ versions.  Don't use those in a C program.  The C versions are
```

#include <time.h>
#include <stdlib.h>

```
Note that the time function takes a pointer argument, so your code won't work as it is written.  You can fix it by replacing time() with **time(NULL)**.

---

### Post by Samanathon on 2008-10-12
That's exactly what I was looking for! Thanks a lot!

---

