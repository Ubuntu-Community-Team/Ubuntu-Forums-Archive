---
title: "shared memory in C"
date: 2008-04-17
forum: Programming Talk
---

### Post by g3k0 on 2008-04-17
Greetings,  I am currently writing a program involving shared memory calls like shmget, shmat, etc.  

for some reason when i do 
    *(my_shm_ptr+5) = 9.8;
    printf("\nHere:%f\n",*(my_shm_ptr+5));

It appears as 0

but when i use %d (integer obviously, I know that) it does display 9;

why can't I save it as a float there?  It is definitely allocated.:confused:

---

### Post by WW on 2008-04-17
Your problem has nothing to do with shared memory. I suspect you declared my_shm_ptr to be a pointer to an int.  If that is the case, then when you assign the value 9.8, it is truncated to 9.  The real problem is that you give a %f format in printf(), but the corresponding argument is not a float.

How did you declare my_shm_ptr?

---

### Post by g3k0 on 2008-04-17
actually technically it is a char*  I just dont understand what exactly is going on with these calls.  How they work etc.  I may need to make a new one for floats.  Im just not sure what is going on.  It works fine with integers.

```

void run_child(int me, int shm_handle) {
    char *my_shm_ptr;
    int i, m;
    unsigned int shm_flag = 00;

    sleep(1);

/* Add the memory to this process's address space */
    my_shm_ptr = (char *) shmat(shm_handle, 0, 0);
    if(my_shm_ptr == (char *) -1) {
        //printf("child[%d]: Shared memory attach failed\n", me);
        exit(0);
    }
    //printf("Child[%d]: shmat[%d] succeeded\n", me, me);

/* Do work, share results with parent via shared memory */
    m = SHM_SIZE/4;
    
    //MY SUCCESSIVE OVERRELAXATION
    float num = 0; //keeps track of the numbers being multiplied
    float x = 0; //Share this as the multiplication #
    for (i = 0; i < 4; ++i){
	    if (i!=me){
		    num = num - (*(my_shm_ptr+i) * x);
	    }
    }
    x = *(my_shm_ptr+4) - num;
    if (*(my_shm_ptr+me) != 0){
	x = x / *(my_shm_ptr+me) ;
    } else {printf("\nDivide by 0 error\n"); }
    *(my_shm_ptr+5) =1980;
    printf("\nHere:%f\n",  *(my_shm_ptr+5));
    //////////////////////////////////////////////////////////////

/* Detach shared memory */
    shmdt(my_shm_ptr);
    if(my_shm_ptr == (char *) -1) {
        printf("child[%d]: Shared memory detach failed\n", me);
        exit(0);
    }

```

---

### Post by smartbei on 2008-04-17
Try changing:
```

*(my_shm_ptr+5) = 9.8;

```
To:
```

*((float *) (my_shm_ptr+5)) = 9.8;

```

---

### Post by g3k0 on 2008-04-17
still 0 :(

---

### Post by WW on 2008-04-17
> **smartbei said:**
> 
```

*((float *) (my_shm_ptr+5)) = 9.8;

```
That cast is too late.  It would have to be something like
```

*( (float *) my_shm_ptr + 5 )  = 9.8;

```
to get the pointer arithmetic to work correctly.

It would be better to change the declaration of my_shm_ptr to
```

float *my_shm_ptr;

```
and tweak the rest of the code where necessary. The line
```

m = SHM_SIZE/4;

```
suggests that the numbers stored in the shared memory each use 4 bytes.  On my computer, a float is 4 bytes, so this should still work.

---

### Post by g3k0 on 2008-04-17
heh, well I got it to work by changing it to float but it took alot of casting all over the place.  Thanks for the help

---

