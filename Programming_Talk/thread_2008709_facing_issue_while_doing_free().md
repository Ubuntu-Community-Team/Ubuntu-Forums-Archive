---
title: "facing issue while doing free()"
date: 2012-06-23
forum: Programming Talk
---

### Post by spanlength1 on 2012-06-23
I am doing a small assignment , where I am facing some issues as I dont have the flexibility to change the function return type.


```

#ifndef AS_C_SKELETON_H
#define AS_C_SKELETON_H

#include "joint.h"
#include <stddef.h>


typedef struct {
  char* name;
  struct Joint** jointArray;
  size_t numJoints;
} Skeleton;


// Creates new skeleton with given name and size
// Name should be deep copied
// Allocates space for given number of joints to jointArray
// Fills the array with NULL values
Skeleton createSkeleton(const char* name, size_t numJoints);

// frees all memory allocated to the skeleton struct
void destroySkeleton(Skeleton skeleton);

#endif

```


skeleton.c file below

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>
#include <assert.h>
#include <math.h>
#include "joint.h"
#include "skeleton.h"

// Creates new skeleton with given name and size
// Name should be deep copied
// Allocates space for given number of joints to jointArray
// Fills the array with NULL values
Skeleton createSkeleton(const char* name, size_t numJoints)
{
        Skeleton *newSkeleton = malloc(sizeof(Skeleton));
        size_t len = 1 + strlen(name);
        char *deepCopyString = malloc(len);
        newSkeleton->name = deepCopyString ? memcpy(deepCopyString, name, len) : NULL;
	newSkeleton->jointArray = malloc(numJoints* sizeof(struct Joint*) );
	newSkeleton->numJoints = numJoints;
        for (unsigned int i = 0 ; i < numJoints ; i++ ){
            newSkeleton->jointArray[i] = NULL;
        }
        return *newSkeleton;
}

// frees all memory allocated to the skeleton struct
void destroySkeleton(Skeleton skeleton)
{
	free(skeleton.name);
        for (unsigned int i = 0 ; i < skeleton.numJoints ; i++){
            destroyJoint(skeleton.jointArray[i]);
        }
        free(skeleton.jointArray);
        free(skeleton);
}


```

main.c 

```

#include <stdio.h>
#include <stdlib.h>
#include "joint.h"
#include "skeleton.h"

int main() {

    Skeleton newSkeleton = createSkeleton("New Skeleton 1", 10);

    destroySkeleton(newSkeleton);

    return 0;
}

```

While the destroySkeleton function executes it gives error 
that free(skeleton) is not valid. Also the *newSkeleton is getting leaked. How to solve the issue. Please help. Function signatures cannot be changed.Valgrind error log below


==12869== HEAP SUMMARY:
==12869==     in use at exit: 12 bytes in 1 blocks
==12869==   total heap usage: 11 allocs, 10 frees, 193 bytes allocated
==12869== 
==12869== Searching for pointers to 1 not-freed blocks
==12869== Checked 56,660 bytes
==12869== 
==12869== 12 bytes in 1 blocks are definitely lost in loss record 1 of 1
==12869==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==12869==    by 0x8048579: createSkeleton (skeleton.c:16)
==12869==    by 0x80489FF: main (main.c:24)
==12869== 
==12869== LEAK SUMMARY:
==12869==    definitely lost: 12 bytes in 1 blocks
==12869==    indirectly lost: 0 bytes in 0 blocks
==12869==      possibly lost: 0 bytes in 0 blocks
==12869==    still reachable: 0 bytes in 0 blocks
==12869==         suppressed: 0 bytes in 0 blocks
==12869== 
==12869== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 12 from 7)

---

### Post by ofnuts on 2012-06-23
The "skeleton" as seen in main() is not  a pointer to allocated memory... it's actually a stack variable, so you don't need to free it. In fact in createSkeleton() it doesn't need to be allocated via malloc(). Just create it on the stack and return it to you caller, the compiler will generate a shallow copy.

---

### Post by dwhitney67 on 2012-06-23
> **spanlength1 said:**
> 
While the destroySkeleton function executes it gives error 
that free(skeleton) is not valid.

You executed the code?  When I attempt to compile it, the following error is produced, thus negating the possibility of getting an file that can be executed.
```

gcc -Wall -pedantic -std=c99 main.c skeleton.c joint.c
skeleton.c: In function &#8216;destroySkeleton&#8217;:
skeleton.c:36:9: error: incompatible type for argument 1 of &#8216;free&#8217;
/usr/include/stdlib.h:488:13: note: expected &#8216;void *&#8217; but argument is of type &#8216;Skeleton&#8217;

```
(Note:  I threw together a "basic" Joint structure and related function since they were not provided, so that I could produce the error above.)

> **spanlength1 said:**
> 
How to solve the issue. Please help. Function signatures cannot be changed.

Why can't the function signatures be changed??  Is this a school assignment?

Anyhow, as ofnuts stated, you can declare the Skeleton object on the stack, both in main() and in createSkeleton().  You would also need to modify destroySkeleton() to remove the last call to free(), for it would not be necessary.

---

