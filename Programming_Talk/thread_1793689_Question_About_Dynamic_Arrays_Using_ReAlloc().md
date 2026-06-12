---
title: "Question About Dynamic Arrays Using ReAlloc()"
date: 2011-06-29
forum: Programming Talk
---

### Post by emiller12345 on 2011-06-29
I was hoping someone could help me understanding the realloc() function  so I can dynamically change the size of my array as my program  progresses...

```
#include <stdlib.h>

int main(int argc, char *argv[]){
  int i=0;
  struct timeval *my_array;
  int my_array_len=0;
  my_array = (struct timeval *)malloc (sizeof(struct timeval) );
  for(i=0; i < 999999999999999; i++){
    int randvar = rand();
    if(randvar > 100){
      //increase size of array <missing>
      struct timeval timev;
      gettimeofday( &timev, NULL );
      my_array[my_array_len++] = timev;
      printf("%i\n", my_array_len);
    }
  }
  return 0;
}

```

---

### Post by psusi on 2011-06-29
Did you read the man page?  What part don't you understand?

---

### Post by emiller12345 on 2011-06-29
From my understanding of this, I should be able to do this...
```
int main(int argc, char *argv[]){
  int i=0;
  struct timeval *my_array;
  int my_array_len=0;
  my_array = (struct timeval *)malloc (sizeof(struct timeval) );
  for(i=0; i < 999999999999999; i++){
    int randvar = rand();
    if(randvar > 100){
      my_array = (struct timeval *)realloc(my_array, my_array_len*sizeof(struct timeval));
      struct timeval timev;
      gettimeofday( &timev, NULL );
      my_array[my_array_len++] = timev;
      printf("%i\n", my_array_len);
    }
  }
  return 0;
}

```
But I get this
Segmentation fault
and I don't know why

---

### Post by emiller12345 on 2011-06-29
Doh, I think I just solved my own noobish problem.

```
int main(int argc, char *argv[]){
  int i=0;
  struct timeval *my_array;
  int my_array_len=0;
  my_array = (struct timeval *)malloc (sizeof(struct timeval) );
  for(i=0; i < 999999999999999; i++){
    int randvar = rand();
    if(randvar > 100){
      my_array = (struct timeval *)realloc(my_array, (my_array_len+1)*sizeof(struct timeval));
      struct timeval timev;
      gettimeofday( &timev, NULL );
      my_array[my_array_len++] = timev;
      printf("%i\n", my_array_len);
    }
  }
  return 0;
}

```
I was reallocing it to zero size then trying to write to the var.

Thanks

---

### Post by dwhitney67 on 2011-06-29
Here's another example of using malloc() and realloc(); note how it is not necessary to apply casts to their return values.  Also, note that I chose to increment the number of elements *prior* to performing the allocation.
```

#include <stdlib.h>
#include <stdio.h>

int main(int argc, char* argv[])
{
   int   array_len = 0;
   char* array = NULL;

   for (int i = 0; i < 26; i++)
   {
      ++array_len;

      if (i == 0)
      {
         array = malloc(array_len * sizeof(char));
      }
      else
      {
         array = realloc(array, array_len * sizeof(char));
      }

      array[array_len - 1] = 'a' + i;

      printf("array_len = %i\n", array_len);
   }

   ++array_len;
   array = realloc(array, array_len * sizeof(char));

   array[array_len - 1] = '\0';

   printf("array = %s\n", array);

   return 0;
}

```

---

### Post by ddimit on 2011-06-30
> **dwhitney67 said:**
> Here's another example of using malloc() and realloc(); note how it is not necessary to apply casts to their return values.  Also, note that I chose to increment the number of elements *prior* to performing the allocation.
```

#include <stdlib.h>
#include <stdio.h>

int main(int argc, char* argv[])
{
   int   array_len = 0;
   char* array = NULL;

   for (int i = 0; i < 26; i++)
   {
      ++array_len;

      if (i == 0)
      {
         array = malloc(array_len * sizeof(char));
      }
      else
      {
         array = realloc(array, array_len * sizeof(char));
      }

      array[array_len - 1] = 'a' + i;

      printf("array_len = %i\n", array_len);
   }

   ++array_len;
   array = realloc(array, array_len * sizeof(char));

   array[array_len - 1] = '\0';

   printf("array = %s\n", array);

   return 0;
}

```


hey im compiling that in visual studio 2010 and comes with that error message
(25): error C2440: '=' : cannot convert from 'void *' to 'char *'
the  error is on these sentences 
array = realloc(...
and 
array = malloc(..

---

### Post by dwhitney67 on 2011-06-30
> **ddimit said:**
> hey im compiling that in visual studio 2010 and comes with that error message
(25): error C2440: '=' : cannot convert from 'void *' to 'char *'
the  error is on these sentences 
array = realloc(...
and 
array = malloc(..

My bad; being that this is the Ubuntu Forums, I assumed you were using Linux.  If M$ requires you to perform the cast, then I guess you must do it.

---

### Post by emiller12345 on 2011-06-30
Thank you ddimit.  That is a really good example of what I'm trying to learn. Now this is a char array, where each item is only one byte in size.  But can I also use this to work with dynamic arrays of any size? like a 1d array of some kind of struct? say I have
```

struct pointxy{
  int x;
  int y;
};

```edit: I'm wondering more about if I need to terminate the 1d array with a '\0' and how I'd go about doing that...
```
#include <stdlib.h>
#include <stdio.h>

struct pointxy{
  int x;
  int y;
};

int main(int argc, char* argv[])
{
   int i = 0;
   int   array_len = 0;
   struct pointxy *array = NULL;
   for (i = 0; i < 26; i++)
   {
      ++array_len;
      if (i == 0)
      {
         array = malloc(array_len * sizeof(struct pointxy));
      }
      else
      {
         array = realloc(array, array_len * sizeof(struct pointxy));
      }
      (array[array_len - 1]).x = 100 + i;
      (array[array_len - 1]).y = 200 + i;
      printf("array_len = %i\n", array_len);
   }
   //++array_len;
   //array = realloc(array, array_len * sizeof(struct pointxy));
   //array[array_len - 1] = '\0';
   for (i = 0; i < 26; i++)
   {
      printf("array[%i] = (%i, %i)\n", i, array[i].x, array[i].y );
   }
   return 0;
}
```

---

### Post by dwhitney67 on 2011-06-30
> **emiller12345 said:**
> edit: I'm wondering more about if I need to terminate the 1d array with a '\0' and how I'd go about doing that...

Only strings need to be null-character terminated.  If you should need to terminate a structure (say a linked list) will a NULL, do not confuse such with a null-character.

---

### Post by emiller12345 on 2011-06-30
> **dwhitney67 said:**
> Only strings need to be null-character terminated.  If you should need to terminate a structure (say a linked list) will a NULL, do not confuse such with a null-character.
Ah I see.  Also if I set the last item in the list to NULL, I think that I may be able to use that as a marker for the current end of the array.
```

int i =0;
while(array[i] != NULL){
  i++;
}
printf("size of array is %i\n", i);

```as long as there are no NULL elements used earlier in the array.
edit: I guess that doesn't work.

---

### Post by psusi on 2011-06-30
NULL is a pointer.  Since your array is not pointers, you can not put a NULL in it.

---

### Post by dwhitney67 on 2011-06-30
> **emiller12345 said:**
> 
edit: I guess that doesn't work.

Works great in this example:
```

#include <stdio.h>

int main(int argc, char* argv[], char* envp[])
{
   while (*envp != NULL)
   {
      printf("%s\n", *envp++);
   }
   return 0;
}

```

---

### Post by psusi on 2011-06-30
> **dwhitney67 said:**
> Works great in this example:


That is because envp is an array of pointers.

---

### Post by dwhitney67 on 2011-06-30
> **psusi said:**
> That is because envp is an array of pointers.

Damn... and I thought it was an array of oranges.

---

### Post by psusi on 2011-07-01
> **dwhitney67 said:**
> Damn... and I thought it was an array of oranges.

By your snarky comment, I assume you don't understand why I said that.  I said that to explain why your envp example did not contradict this statement:

> NULL is a pointer. Since your array is not pointers, you can not put a NULL in it.

I thought the reason you showed the envp example was to contradict that statement.  Was there some other purpose?

---

### Post by johnl on 2011-07-01
```

      if (i == 0)
      {
         array = malloc(array_len * sizeof(struct pointxy));
      }
      else
      {
         array = realloc(array, array_len * sizeof(struct pointxy));
      }

```

Just a note -- you can simplify this -- if you pass NULL as the first argument to realloc it behaves like malloc, so as long as you initialize array to NULL, you don't need to distinguish between the first allocation and subsequent reallocations.

---

### Post by dwhitney67 on 2011-07-01
> **psusi said:**
> 
I thought the reason you showed the envp example was to contradict that statement.  Was there some other purpose?
I was not contradicting your statement; I was attempting to inform the OP that NULL does have it's uses.  (see my post where I quoted him/her).

As for your previous post, yes, you were correct in that the array being used by the OP probably int values, and thus comparing it to NULL made no sense.  I could not tell how the array was declared (that part was not included), but I assumed, as you did, that the OP was continuing with their original example.  Needless to say, if I had seen a problem with your response, I would have said something.

---

### Post by dwhitney67 on 2011-07-01
> **johnl said:**
> 
Just a note -- you can simplify this -- if you pass NULL as the first argument to realloc it behaves like malloc, so as long as you initialize array to NULL, you don't need to distinguish between the first allocation and subsequent reallocations.

Thanks for pointing that out.

---

