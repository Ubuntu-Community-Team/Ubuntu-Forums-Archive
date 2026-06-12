---
title: "Basic Questions about for loops in C"
date: 2011-08-17
forum: Programming Talk
---

### Post by kevinharper on 2011-08-17
I always thought that an int var (counter) should be declared if it will be used in a for loop. As follows:
```

#include <stdio.h>
#include <stdlib.h>

#define MAX 5

int main( void )
{
   int i;

   for( i = 0; i < MAX; i++ )
      /* statements */

   return EXIT_SUCCESS;
}

```
I was recently told, however, that the declaration & the initialization can (and should) be done simultaneously within the for() statement. Example:
```

#include <stdio.h>
#include <stdlib.h>

#define MAX 5

int main( void )
{
   for( i = 0; i < MAX; i++ )
      /* statements */

   return EXIT_SUCCESS;
}

```
Looking at all sorts of online tutorials and code fragments in different forums I've noticed that most everyone does as is on the first code example.

I know the second compiles w/out errors and executes properly.

Questions:
Which is cleaner?
Which is more widely accepted/used?
Which is more correct, I guess is what I'm trying to get at?

---

### Post by era86 on 2011-08-18
I'll be honest, in C I have never seen a for loop work without initializing the int variable first.

In fact, I cannot get this code to compile:

[PHP]
#include <stdio.h>

#define MAX 5

int main(void) {
        for (i = 0; i < MAX; i++) {
                printf("Test\n");
        }
        return 0;
}
[/PHP]

---

### Post by karlson on 2011-08-18
> **kevinharper said:**
> 
Questions:
Which is cleaner?


No difference.   Just run
```

gcc -std=c99 -S <file>

```

> 
Which is more widely accepted/used?


The inline declaration was more commonly used in C++ then in C.

> 
Which is more correct, I guess is what I'm trying to get at?

The predeclaration of variables is an older standard and more commonly used in C programs and the inline declaration requires an explicit flag to be set for GCC so just from the point of view of laziness I'd use the older way.

---

### Post by lisati on 2011-08-18
I suspect that the "best" answer will depend on how clear the code will be to you or someone else when the time comes to maintain it 6 months or more down the track.

---

### Post by karlson on 2011-08-18
> **era86 said:**
> I'll be honest, in C I have never seen a for loop work without initializing the int variable first.

In fact, I cannot get this code to compile:

[PHP]
#include <stdio.h>

#define MAX 5

int main(void) {
        for (i = 0; i < MAX; i++) {
                printf("Test\n");
        }
        return 0;
}
[/PHP]


Because code has to read:
```

for(int i = 0; i < MAX ; i++)

```

and to compile it you need to do

```

gcc -std=c99 <file>

```

---

### Post by ofnuts on 2011-08-18
> **era86 said:**
> I'll be honest, in C I have never seen a for loop work without initializing the int variable first.

In fact, I cannot get this code to compile:

[PHP]
#include <stdio.h>

#define MAX 5

int main(void) {
        for (i = 0; i < MAX; i++) {
                printf("Test\n");
        }
        return 0;
}
[/PHP]

One of the reason is that if you declare the  loop counter inside the for(...), it is unavailable outside the loop. And testing the counter against the loop limit is a good way to know if the loop was exited early:
[php]
int i;
for(i=0;i<MAX;i++) {
    if (some_condition) break;
}
if (i==MAX) { 
    /* got the full loop */
} else {
    /* exited early */
}
[/php]

---

### Post by Bachstelze on 2011-08-18
It's really a matter of preference. As I said, to me the second one is cleaner because you don't have the counter variable just sitting there between loops when it is not needed. As for testing if the loop exited early, I never use break in for loops. To me a for loop is supposed to always be executed "in full". If there's chance that it need to be exited early, I use a while.

---

### Post by johnl on 2011-08-18
This syntax:

```

for(int i = 0; i < 100; ++i) {

}

```

Is part of the C99 standard.  Your compiler will need to support C99 (or have an extension for this behavior) to use it.  Prior to C99, you would always see this written according to the C89 standard:

```

int i;

for(i = 0; i < 100; ++i) {

}

```

You can test this with GCC:

```

~/Projects/test$ gcc -std=c89 -pedantic -Wall test.c -o test
test.c: In function ‘main’:
test.c:5:5: error: ‘for’ loop initial declarations are only allowed in C99 mode
test.c:5:5: note: use option -std=c99 or -std=gnu99 to compile your code
~/Projects/test$ gcc -std=c99 -pedantic -Wall test.c -o test
(compiles successfully)

```

In fact, according to C89, all variable declarations must be done prior to any code in a block, so the following:


```

int x = 10;
printf("x = %d\n", x);
int y;

```

is not valid.

With that said, most compilers support C99 (Microsoft's Visual Studio C compiler being a notable exception) and those that don't likely already included these two things as extensions.

---

### Post by kevinharper on 2011-08-18
Okay...

I usually compile with "gcc -std=c99 -pedantic -Wall -Werror -o file file.c"

I like the explanation that Bachstelze gave. This way the var is basically nonexistent outside of the for loop. I also agree with him in that a for loop should basically execute until condition is FALSE.

I apologize... I hadn't noticed that I needed to include the "int" inside the declaration/initialization. And, as noted, this is why the code I included in my first wouldn't compile.

Thanks for the responses guys. Have an awesome Friday.

---

