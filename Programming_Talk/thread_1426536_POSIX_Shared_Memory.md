---
title: "POSIX Shared Memory"
date: 2010-03-10
forum: Programming Talk
---

### Post by safarin on 2010-03-10
Hi all, I very new in linux and programming.. 

Do anybody here can help me to clear my thought, I want to store the data of float into shared memory..

My questions are:

1. To store the float data, is this data need to change into string or char before simply save into shared memory..

2. Is each data is for one id?? I mean, If there are more than one data is this shared memory need to shmget, shmat for each data? 
If No, how to?

3. Could anybody tell me the basic concepts behind this shared memory? I already read from many web page.. but I not clear at all.

Sorry for my English.. ;)

---

### Post by dwhitney67 on 2010-03-10
To answer your first question, yes you can store a float in shared-memory.  The shared-memory should not be considered any different from the regular system memory that you use.  The only difference is that the shared-memory can be accessed by multiple processes.

Personally, I would recommend that you define a structure to contain the data you want to share between processes, even if it is a mere float value.  For example:
```

struct MySharedData
{
   float value;
};

```

A process will need to setup the shared memory segment, and another process will need to attach to it.  Once this takes place, each process may interchange data.

To setup the shared memory, something like this is needed (I'll let you worry about including the appropriate header files):
```

key_t key = 1234;

/* create shared memory of a particular size */
int shmid = shmget(key, sizeof(struct MySharedData), IPC_CREAT | 0666);

if (shmid < 0)
{
   perror("shmget");
   return -1;
}

/* attach/map shared memory to our data type */
struct MySharedData* data = (struct MySharedData*) shmat(shmid, NULL, 0);

if (data == -1)
{
   perror("shmat");
   return -1;
}

...

data->value = 123.56789;

...

/* detach from shared memory */
if (shmdt(data) < 0)
{
   perror("shmdt");
   return -1;
}

/* destroy shared memory (important!!!) */
if (shmctl(shmid, IPC_RMID, NULL) < 0)
{
   perror("shmctl");
   return -1;
}

```

To attach to an existing shared memory segment, do something like:
```

key_t key = 1234;

int shmid = shmget(key, sizeof(struct MySharedData), 0666);

if (shmid < 0)
{
   perror("shmget");
   return -1;
}

struct MySharedData* data = (struct MySharedData*) shmat(shmid, NULL, 0);

if (data == -1)
{
   perror("shmat");
   return -1;
}

printf("shared float data = %f\n", data->value);

data->value = 0.123;

...

/* although not required, it is a good idea to detach */
if (shmdt(data) < 0)
{
   perror("shmdt");
   return -1;
}

```

I hope this helps; happy coding!

---

### Post by safarin on 2010-03-10
Thank you dwhitney67,

I still not clear, for an example if I have float val [3] , which are val [0] = 123.45, val [1] = 678.90 and val [2] = 1011.12.. and I want to save into shared memory do I really need struct? I still don't have knowledge of struct.. hehehe.. and what the meaning of data->value? For "size_t size" the size is based on every each or val.. or the overall val??

---

### Post by Xyro on 2010-03-10
You do not need to have your data in a struct, but it is much cleaner to do it that way. The pointer that is returned to your program by shmat() is a pointer to a chunk of memory (of whatever size you've asked for) and you can do with it whatever you wish. For example (with no struct):
```

...

float *ptr = NULL;
float val[3];

val[0] = 123.45; 
val[1] = 678.90;
val[2] = 1011.12;

ptr = shmat( ... ); // Assuming you've got the arguments of shmat() all worked out...


// Assuming you've requested (and successfully received) a
// 3 float value sized shared memory segment.
ptr[0] = val[0];
ptr[1] = val[1];
ptr[2] = val[2];

...

```

Now the first 3 floats in your shared memory segment are the values 123.45, 678.90 and 1011.12

---

### Post by dwhitney67 on 2010-03-10
Thanks Xyro for assisting with the follow-up.  In case the OP is still confused, the shared-memory is setup similar to the following:
```

float val[3];

int shmid = shmget(key, sizeof(val), IPC_CREAT | 0666);

```
This should setup a shared-memory segment of 12 bytes long (4 bytes for each float in the array).

---

### Post by safarin on 2010-03-10
Thank you very much dwhitney67 and Xyro..

Problem solved!!!

:D:D:D:D:D:D:D:D

---

