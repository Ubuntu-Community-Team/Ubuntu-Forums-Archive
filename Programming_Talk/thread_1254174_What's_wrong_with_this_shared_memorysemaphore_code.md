---
title: "What's wrong with this shared memory/semaphore code?"
date: 2009-08-31
forum: Programming Talk
---

### Post by OutOfReach on 2009-08-31
I'm playing around with semaphore/shared memory, I wrote this code, but it doesn't seem to be working (i.e. the integer value doesn't appear to get increased by each client, run it and you'll see what I mean)
[PHP]
#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/mman.h>
#include <sys/stat.h>
#include <semaphore.h>

// Prototypes
sem_t *open_semaphore(char *sem_name);
int open_shared_memory_segment(char *shm_name);

int main(int argc, char** argv)
{
	char *semaphore_name = "/testing_semaphore";
    char *shared_mem_name = "/testing_shared_memory";
    sem_t *sem_addr;
    int shared_mem_segment = 0;
    int *mem_segment = NULL;
    
    sem_addr = open_semaphore(semaphore_name);
    if (sem_addr == NULL)
    {
        printf("Getting semaphore failed.\n");
        exit(EXIT_FAILURE);
    }
    shared_mem_segment = open_shared_memory_segment(shared_mem_name);
    if (shared_mem_segment == -1)
    {
        printf("Getting shared memory segment failed\n");
        exit(EXIT_FAILURE);
    }
    
    mem_segment = mmap(NULL, sizeof(int), PROT_READ | PROT_WRITE, MAP_SHARED, shared_mem_segment, 0);
    if (mem_segment == MAP_FAILED) {
        printf("Failed to map memory, aborting.\n");
        exit(EXIT_FAILURE);
    }
    
    int counter = 0;
    while (counter < 20)
    {
        sem_wait(sem_addr);
        printf("[Client] Current integer in memory: %i\n", *mem_segment);
        (*mem_segment)++;
        counter++;
        sem_post(sem_addr);
        msync(mem_segment, sizeof(int), MS_SYNC|MS_INVALIDATE);
        sleep(3);
    }
	return 0;
}

sem_t *open_semaphore(char *sem_name)
{
    sem_t *return_value;
    return_value = sem_open(sem_name, O_CREAT, 0666, 1);
    if (return_value == SEM_FAILED)
    {
        return NULL;
    }
    sem_unlink(sem_name);
    return return_value;
}

int open_shared_memory_segment(char *shm_name)
{
    int fd = 0;
    fd = shm_open(shm_name, O_RDWR | O_CREAT, 0666);
    if (fd == -1)
        return -1;
    ftruncate(fd, sizeof(int));
        
    shm_unlink(shm_name);
    return fd;
}
[/PHP]

What am I doing wrong? Thanks!

---

### Post by Fallen_Demon on 2009-08-31
I'm not entirely sure, but shouldn't
```

sem_wait(sem_addr);
        printf("[Client] Current integer in memory: %i\n", *mem_segment);
        (*mem_segment)++;
        counter++;
        sem_post(sem_addr);
        msync(mem_segment, sizeof(int), MS_SYNC|MS_INVALIDATE);
        sleep(3); 

```

be

```

sem_wait(sem_addr);
        printf("[Client] Current integer in memory: %i\n", *mem_segment);
        *(*mem_segment)++;
        counter++;
        sem_post(sem_addr);
        msync(mem_segment, sizeof(int), MS_SYNC|MS_INVALIDATE);
        sleep(3); 

```

Sorry, not good with pointers :( It may also help to declare mem_segment as volatile

---

### Post by OutOfReach on 2009-08-31
> **Fallen_Demon said:**
> I'm not entirely sure, but shouldn't
```

sem_wait(sem_addr);
        printf("[Client] Current integer in memory: %i\n", *mem_segment);
        (*mem_segment)++;
        counter++;
        sem_post(sem_addr);
        msync(mem_segment, sizeof(int), MS_SYNC|MS_INVALIDATE);
        sleep(3); 

```

be

```

sem_wait(sem_addr);
        printf("[Client] Current integer in memory: %i\n", *mem_segment);
        *(*mem_segment)++;
        counter++;
        sem_post(sem_addr);
        msync(mem_segment, sizeof(int), MS_SYNC|MS_INVALIDATE);
        sleep(3); 

```

Sorry, not good with pointers :( It may also help to declare mem_segment as volatile

hmm, nope, just tried it and it's not working. Thanks though!

---

### Post by OutOfReach on 2009-08-31
Bump

---

### Post by mr_e_uss on 2009-08-31
Hmmmm.  I compiled your source, and the results were what you intended:

```

~/tmp$ ./shmem 
[Client] Current integer in memory: 0
[Client] Current integer in memory: 1
[Client] Current integer in memory: 2
[Client] Current integer in memory: 3
[Client] Current integer in memory: 4
[Client] Current integer in memory: 5
[Client] Current integer in memory: 6
[Client] Current integer in memory: 7
[Client] Current integer in memory: 8
[Client] Current integer in memory: 9
[Client] Current integer in memory: 10
[Client] Current integer in memory: 11
[Client] Current integer in memory: 12
[Client] Current integer in memory: 13
[Client] Current integer in memory: 14
[Client] Current integer in memory: 15
[Client] Current integer in memory: 16
[Client] Current integer in memory: 17
[Client] Current integer in memory: 18
[Client] Current integer in memory: 19
~/tmp$ 

```

---

### Post by OutOfReach on 2009-08-31
> **mr_e_uss said:**
> Hmmmm.  I compiled your source, and the results were what you intended:

```

~/tmp$ ./shmem 
[Client] Current integer in memory: 0
[Client] Current integer in memory: 1
[Client] Current integer in memory: 2
[Client] Current integer in memory: 3
[Client] Current integer in memory: 4
[Client] Current integer in memory: 5
[Client] Current integer in memory: 6
[Client] Current integer in memory: 7
[Client] Current integer in memory: 8
[Client] Current integer in memory: 9
[Client] Current integer in memory: 10
[Client] Current integer in memory: 11
[Client] Current integer in memory: 12
[Client] Current integer in memory: 13
[Client] Current integer in memory: 14
[Client] Current integer in memory: 15
[Client] Current integer in memory: 16
[Client] Current integer in memory: 17
[Client] Current integer in memory: 18
[Client] Current integer in memory: 19
~/tmp$ 

```

Run the program in 2 seperate windows, one of them a little after the first one, they should be synced but it isn't so.

---

### Post by mr_e_uss on 2009-08-31
Ahh -- now I understand.

I think you are missing a call to mmap(), after the ftruncate() call.  Also, and more importantly, the call to shm_unlink() might be happening too soon.

See these links:
[http://www.opengroup.org/onlinepubs/000095399/functions/shm_unlink.html](http://www.opengroup.org/onlinepubs/000095399/functions/shm_unlink.html)
[http://mij.oltrelinux.com/devel/unixprg/#ipc__posix_shm](http://mij.oltrelinux.com/devel/unixprg/#ipc__posix_shm)

---

### Post by mr_e_uss on 2009-08-31
Yep -- the unlinks were the problem.

I moved BOTH unlink operations from within the open...() calls to the main routine (just before the "return 0;").

Of course, you have to use the correct symbols for the names.  Here's the code:

```

#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/mman.h>
#include <sys/stat.h>
#include <semaphore.h>

// Prototypes
sem_t *open_semaphore(char *sem_name);
int open_shared_memory_segment(char *shm_name);

int main(int argc, char** argv)
{
    char *semaphore_name = "/testing_semaphore";
    char *shared_mem_name = "/testing_shared_memory";
    sem_t *sem_addr;
    int shared_mem_segment = 0;
    int *mem_segment = NULL;
    
    sem_addr = open_semaphore(semaphore_name);
    if (sem_addr == NULL)
    {
        printf("Getting semaphore failed.\n");
        exit(EXIT_FAILURE);
    }
    shared_mem_segment = open_shared_memory_segment(shared_mem_name);
    if (shared_mem_segment == -1)
    {
        printf("Getting shared memory segment failed\n");
        exit(EXIT_FAILURE);
    }
    
    mem_segment = mmap(NULL, sizeof(int), PROT_READ | PROT_WRITE, MAP_SHARED, shared_mem_segment, 0);
    if (mem_segment == MAP_FAILED) {
        printf("Failed to map memory, aborting.\n");
        exit(EXIT_FAILURE);
    }
    
    int counter = 0;
    while (counter < 20)
    {
        sem_wait(sem_addr);
        printf("[Client] Current integer in memory: %i\n", *mem_segment);
        (*mem_segment)++;
        counter++;
        sem_post(sem_addr);
        msync(mem_segment, sizeof(int), MS_SYNC|MS_INVALIDATE);
        sleep(3);
    }
    shm_unlink(shared_mem_name);
    sem_unlink(semaphore_name);
    return 0;
}

sem_t *open_semaphore(char *sem_name)
{
    sem_t *return_value;
    return_value = sem_open(sem_name, O_CREAT, 0666, 1);
    if (return_value == SEM_FAILED)
    {
        return NULL;
    }
    return return_value;
}

int open_shared_memory_segment(char *shm_name)
{
    int fd = 0;
    fd = shm_open(shm_name, O_RDWR | O_CREAT, 0666);
    if (fd == -1)
        return -1;
    ftruncate(fd, sizeof(int));
        
    return fd;
}  

```

---

### Post by OutOfReach on 2009-08-31
> **mr_e_uss said:**
> Yep -- the unlinks were the problem.

I moved BOTH unlink operations from within the open...() calls to the main routine (just before the "return 0;").

Of course, you have to use the correct symbols for the names.  Here's the code:
--SNIP--

Thank you! That worked perfectly, I was really stuck on that one. :)

EDIT: Looks like the SOLVED tags are back, nice!

---

### Post by mr_e_uss on 2009-08-31
You are very welcome.  Good luck...

---

