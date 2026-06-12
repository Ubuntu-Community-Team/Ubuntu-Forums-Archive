---
title: "SegFaul C Heap ~~16k"
date: 2015-01-26
forum: Programming Talk
---

### Post by 3246251196 on 2015-01-26
```

#define RSDL_ARR_MULTIPLE_SIZE 100
typedef Uint32 rSDL_clip_ord_t;
typedef rSDL_clip_ord_t** rSDL_clip_arr_t;

```

```

int
rSDL_insert_clip( rSDL_clip_ord_t* pixel, int arr_index_pointer, rSDL_clip_arr_t** arr )
{
  if( 0 == arr_index_pointer )
  {
    *arr = calloc( RSDL_ARR_MULTIPLE_SIZE, sizeof( rSDL_clip_ord_t* ) );
    if ( NULL == *arr )
    {
      fprintf(stderr,
              "%s: Error allocating memory\n",
              __FUNCTION__);
      return -1;
    }
  }
  else if( 0 == arr_index_pointer % RSDL_ARR_MULTIPLE_SIZE )
  {
    const int RSDL_ARR_MULTIPLY = arr_index_pointer / RSDL_ARR_MULTIPLE_SIZE + 1;
    *arr = realloc( *arr, RSDL_ARR_MULTIPLY * RSDL_ARR_MULTIPLE_SIZE );
    if ( NULL == *arr )
    {
      fprintf(stderr,
              "%s: Error allocating memory\n",
              __FUNCTION__);
      return -1;
    }
  }

  *(*arr + (sizeof(rSDL_clip_ord_t*)*arr_index_pointer)) = pixel;
  return 0;
}

```

Hi, this is mainly for practice reasons. I want to store a contiguous block of elements (each a pointer to a uint32) on the heap. My program seems to crash when arr_index_pointer is ~~ 2083 (I am running 64 bit pointers so this does equate to approximately 16k - I do not know if this helps). FYI: the reason for taking in a rSDL_clip_arr_t** arr is because the program that uses this library contains a global variable which is a ptr to a rSDL_clip_arr_t. The global I just want to point to the heap containing the first address (element) of this huge contiguous array.

Anyway, things seem to work fine but when I get to this value of 207x-208x we get a segfault. As far as I am aware I have the potential heap size of the addressable virtual memory.

I am not interested in the code quality, but why this is happening. Perhaps there is no contiguous space left but I am not getting NULL from realloc... I guess a linked list would be better then.. but perhaps there is something wrong in the code.

Thank you.

---

### Post by spjackson on 2015-01-27
I won't pretend to understand what is going on here, but I will nevertheless make a couple of comments that I hope you find helpful.

1. If realloc returns a value other than NULL it is not guaranteed that the memory is available. See the Notes section from "man realloc".

2. I am not aware of anything special about 16k in normal circumstances. Limits can be imposed via ulimit, but this is unlikely to be the case. Perhaps there is another reason for the segfault. Have you tried valgrind?

---

### Post by 3246251196 on 2015-01-27
Hi Sp, thanks for your reply.

I think it has come to my attention that some changes are needed to the code:

```

int
rSDL_insert_clip( rSDL_clip_ord_t* pixel, int arr_index_pointer, rSDL_clip_arr_t** arr )
{
  if( 0 == arr_index_pointer )
  {
    *arr = calloc( RSDL_ARR_MULTIPLE_SIZE, sizeof( rSDL_clip_ord_t* ) );
    if ( NULL == *arr )
    {
      fprintf(stderr,
              "%s: Error allocating memory\n",
              __FUNCTION__);
      return -1;
    }
  }
  else if( 0 == arr_index_pointer % RSDL_ARR_MULTIPLE_SIZE )
  {
    const int RSDL_ARR_MULTIPLY = arr_index_pointer / RSDL_ARR_MULTIPLE_SIZE + 1;
    *arr = realloc( *arr, RSDL_ARR_MULTIPLY * RSDL_ARR_MULTIPLE_SIZE*** sizeof( rSDL_clip_ord_t* )**)**;**
    if ( NULL == *arr )
    {
      fprintf(stderr,
              "%s: Error allocating memory\n",
              __FUNCTION__);
      return -1;
    }
  }

  *(*arr + [s](sizeof(rSDL_clip_ord_t*)*[/s]arr_index_pointer)) = pixel;
  return 0;
}

```

Firstly, I forgot that C knows how to traverse an array containing elements of size n: I do not have to specify the number of bytes explicitly using sizeof. Also, in my reallocation I am out by a factor of eight. I do not just want 100*2 - for example, I want 100 lots of 2 lots of 8 (size of ptrs). 

I will try this later.

---

### Post by 3246251196 on 2015-01-27
Okay, so the suggested changes have worked.

However, there is something else bugging me. I like to use the -Werror and -Wall flags whenever I can. Well, if I use -Werror compilation fails because of this:

```
124:31: warning: assignment from incompatible pointer type [enabled by default]
```

Perhaps knowing a little more about where this function is called will help. The code shown in previous posts is a shared object used by an application. The application has something like this:

```
rSDL_clip_arr_t* clipping_arr_base; // A GLOBAL VARIABLE
```

And, later on the function is effectively called like this:

```
rSDL_insert_clip( BLAH, BLAH, &clipping_arr_base);
```

Cheers.

---

### Post by spjackson on 2015-01-27
> 
```
124:31: warning: assignment from incompatible pointer type [enabled by default]
```

Please show line 124 of your source code and any declarations relevant to the assignment on that line.

---

### Post by 3246251196 on 2015-01-27
```
*(*arr +arr_index_pointer)) = pixel;
```
Hi, sorry I forgot

---

### Post by 3246251196 on 2015-02-04
Bumping this one just for the explanation...

Anyone?

I know that when I am using malloc and co I should not cast the resulting address - though nothing stops me. So perhaps when I am refering to *arr I am refering to a pointer to void, but I am not allowed the cast the LHS either without an error being raised.

Cheers.

---

### Post by spjackson on 2015-02-04
> **3246251196 said:**
> ```
*(*arr +arr_index_pointer)) = pixel;
```
Hi, sorry I forgot

Your parentheses do not match up - you have one '(' and two ')'. However, I don't see how that results in the warning you mention.

If we match up the parentheses, then the problem seems to be that syntactically you need a further pointer de-reference, e.g.
```

$ cat -n ptr.c 
     1    
     2    typedef unsigned int Uint32;
     3    
     4    typedef Uint32 rSDL_clip_ord_t;
     5    typedef rSDL_clip_ord_t** rSDL_clip_arr_t;
     6    
     7    int main(void)
     8    {
     9        rSDL_clip_ord_t* pixel = 0;
    10        int arr_index_pointer = 0;
    11        rSDL_clip_arr_t** arr = 0;
    12    
    13    
    14        **((*arr) +arr_index_pointer) = pixel; /* ok */
    15    
    16        *((*arr) +arr_index_pointer) = pixel; /* incompatible ptr type */
    17    
    18        return 0;
    19    }
    20    
$ gcc -Wall -o ptr ptr.c
ptr.c: In function &#8216;main&#8217;:
ptr.c:16:34: warning: assignment from incompatible pointer type [enabled by default]
     *((*arr) +arr_index_pointer) = pixel; /* incompatible ptr type */
                                  ^

```
Whether that is what you mean from a semantic point of view is unclear to me.

---

### Post by 3246251196 on 2015-02-08
Hi, thanks for the reply. The reason brackets did not match up was due to a copy and paste issue.

The double derefernce does not create any compilation errors which is good, but that is not what I want.

rSDL_clip_arr_t is a type I want to use because it is an array of pointers to Uint32s. I want to have a contiguous block of pointers to uint32s. So, when I do:

```

 *((*arr) +arr_index_pointer) = pixel; /* incompatible ptr type */

```

I want to assign ptr to uint32 to this element of the contiguous block.

Clearly the design is not great because I am dealing with multiple indirection and it gets messy, but I am still wondering why it is an incompatible pointer type. If I forget about the -Werror/Wall then the compilers complains but things work as I actually want.

Cheers

---

