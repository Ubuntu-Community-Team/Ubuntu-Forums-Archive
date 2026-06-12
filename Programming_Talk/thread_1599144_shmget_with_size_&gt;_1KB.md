---
title: "shmget with size &gt; 1KB"
date: 2010-10-17
forum: Programming Talk
---

### Post by traken on 2010-10-17
I'm having a problem tring to get shmget to allocate a section of memory greater than 1KB.  With the code below, if SHMSZ is 1024, shmget works; if SHMSZ is 1025, it doesn't work (spits out 'shmget: Invalid argument').  'lpcs -l' shows that there shouldn't be a problem with the size.  Any ideas?
```
------ Shared Memory Limits --------
max number of segments = 4096
max seg size (kbytes) = 32768
max total shared memory (kbytes) = 8388608
min seg size (bytes) = 1

```
[php]...

#define SHMSZ 1025

int main( int argc, char** argv )
{
    key_t key = 1234;
    int shmid = -1;

    if ((shmid = shmget( key, SHMSZ, IPC_CREAT | 0666 )) < 0 )
    {
        perror( "shmget" );
        exit( errno );
    }

...
[/php]

Edit:  Apparently actually checking the value of errno can be helpful.  In this case, I was running into EINVAL.  I had previously run the program with the size of 1024, but didn't delete the memory associated with it.  When I ran it with 1025, with the same key, it say the previous memory and threw an error.

Now I just have to find out how to delete shared memory.

---

