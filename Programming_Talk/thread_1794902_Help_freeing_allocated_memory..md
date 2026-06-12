---
title: "Help freeing allocated memory."
date: 2011-07-01
forum: Programming Talk
---

### Post by Rany Albeg on 2011-07-01
It has been a long time since I wrote something in C, and I'm trying to build a vector.
I wrote its constructor and its 'add' method.
Now I want to test it and free the allocated memory after using this vector, but I keep getting a segfault.
I guess my 'free' method is wrong so I need some help with this game of pointers.
Thanks in advance.

[PHP]/**** The vector type ****/
 
typedef struct _rds_vector_t
{
        void** objs; // the vector
        size_t size; // the size of the vector
        size_t numalloc; // number of allocated objects.
 
} rds_vector_t;
 
/**** The constructor ****/
rds_vector_t* rds_vector_new()
{
        rds_vector_t* new_vec;
        if((new_vec = (rds_vector_t*)malloc(sizeof(rds_vector_t))) == NULL)
                rds_vector_failure(__LINE__, "malloc failed.");
 
        new_vec->objs = NULL;
        new_vec->size = new_vec->numalloc = 0;
        
        return new_vec;
}
 
/**** Add method ****/
void rds_vector_add(rds_vector_t* vec, void* obj)
{
        if(!vec->size)
        {
                if((vec->objs = (void**)malloc(sizeof(void*))) == NULL)
                        rds_vector_failure(__LINE__, "malloc failed.");
                vec->objs[0] = obj;
                vec->size = vec->numalloc = 1;
                return;
        }
 
        if (vec->size == vec->numalloc)
                rds_vector_amortization(vec);
 
        vec->objs[vec->numalloc++] = obj;
        return;
}

/**** free method ****/
void rds_vector_free(rds_vector_t* vec)
{
        size_t na = vec->numalloc, i;
 
        for(i=0; i<na; ++i)
        
                free(vec->objs[i]);
 
        free(vec->objs);
}
 
/**** main.c ****/
#include "rds_vector.h"
 
int main(int argc, char** argv)
{
        rds_vector_t* vec = rds_vector_new();
 
        char* arr0= "hello0";
        
        rds_vector_add(vec, arr0);
 
        rds_vector_free(vec);
 
        return EXIT_SUCCESS;
}[/PHP]

Have a good day!

---

### Post by cgroza on 2011-07-01
Compile your code using the -g flag and then use GDB to step through your code.
Do:
```


gdb your_program
break your_function, or file:line
run

```It will tell you when and where your segfault occurs.

You should check a tutorial for gdb, it is a very useful tool. Gets you rid of a lot of headaches in cases like this one.

---

### Post by JupiterV2 on 2011-07-01
> /**** free method ****/ 
void rds_vector_free(rds_vector_t* vec) 
{ 
        size_t na = vec->numalloc, i; 
  
        for(i=0; i<na; ++i) 
         
                free(vec->objs[i]); 
  
        free(vec->objs); 
} 


At first glance, without compiling your code, it looks like you double free vec->objs and fail to free the vector object (vec) itself. valgrind will be of help to you here. You should also NULLify the pointers so they don't point to invalid memory.

---

### Post by Rany Albeg on 2011-07-02
First, thank you for responding to my question.
Problem is partially solved.
I tried to free a memory that I didn't even allocated.

I ran the program with valgrind as suggested and I can see that all memory blocks were freed.

And from that point I wonder if it is a good practice to not allocate as much space as I was thinking I'm allocating.
I'll explain:

As you can see in my 'add' method I'm allocating a space only for void** objs:
```
if((vec->objs = (void**)malloc(sizeof(void*))) == NULL)
```

and then I **just point** to that object I receive within the function, obj, like that:
```
vec->objs[0] = obj;
```

'add' does not actually make another **copy** of this object and store it inside the vector.
It seems that it is impossible to do so, since I don't know the size of the object it receives.

Anyhow, just pointing to that object seems unsafe - if the client frees that address, it is also removed from the vector.

I'm looking for a solution to the pointing issue.
Any help will be appreciated.
Thank you.

---

### Post by JupiterV2 on 2011-07-02
First off, malloc (sizeof (void*)) allocates a single 4 byte chunk of memory. I assume that's what you want, to store a memory address? In your add() function you request another chunk of memory for each new object and assign it to vec->objs. I would be very surprised if valgrind isn't reporting a great number of errors and detecting memory leaks because each time you assign the new block returned by malloc you're orphaning the other memory previously allocated to it. I think what you are wanting to do is to request an initial block of memory for your vec->objs array. Decide on a default/minimum size for your vector, something like: vec->obj = malloc (sizeof (void *) * MIN_VECTOR_LEN); You would then set vec->size to MIN_VECTOR_LEN; and vec->numalloc = 0;, if I understand your code correctly. Then, in your add() function, check to see if your vector is full and realloc() more memory to it and increase vec->size accordingly. It's up to you on how much to increase it but its not uncommon to double the size to minimize the number of allocs/reallocs if its expected the vector's size would have to change often.

Hope that helps.

---

### Post by Rany Albeg on 2011-07-04
Thank you.

---

