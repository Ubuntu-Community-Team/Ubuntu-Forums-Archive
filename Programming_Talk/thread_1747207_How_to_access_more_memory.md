---
title: "How to access more memory"
date: 2011-05-02
forum: Programming Talk
---

### Post by paulr1984 on 2011-05-02
Hi,

I'm writing a program that will need lots of memory.  Is there a way to malloc more than the available RAM and use swap memory?  So far, have tried:

(1) setting vm.overcommit_memory=1 in /etc/sysctl.conf
(2) setting vm.overcommit_ratio=100 in /etc/sysctl.conf
(3) set ulimit memory attributes to "unlimited"

But my application still fails to malloc more than the available RAM.  I was hoping it would use up some of the swap memory.  To give you a better picture, here are some more details:

My System:
Ubuntu 10.10 32-bit on a (64-bit) Macbook Pro
4GB RAM
400GB Disk Space
Intel Core2 Duo 2.4ghz

Malloc'ing more than 2.7gb fails even if I still have 3.5gb free RAM.  I am desperately trying to find a way to enable it to malloc more memory.  Any help will be appreciated.

There probably is a way to do this.  Look at how the memory consumption for applications like Oracle just shoot up.  The application I will be writing is scientific.  Assume for now that I cannot simply break down whatever data I have to fit into memory.

---

### Post by ssam on 2011-05-02
is it due to malloc trying to allocate a continuous block? could use several malloc calls and keep the data in separate arrays.

or maybe look at using mmap

---

### Post by paulr1984 on 2011-05-02
hi ssam,

I've tried to use multiple calls to malloc with smaller data sizes.  But malloc still fails when I get to a total of 2.7gb of allocated memory.  Right now, there is no difference between malloc'ing one large chunk of memory or malloc'ing several smaller chunks of memory.

Why is it that I can't malloc more than 2.7gb of memory but I can run two applications which consume 2.7gb of memory?  When running two instances of my application, it starts to thrash to my swap memory.  How do I make it thrash for a single instance instead having 2*2.7 gb of memory?

---

### Post by jwbrase on 2011-05-02
> **paulr1984 said:**
> My System:
Ubuntu 10.10 **32-bit** on a (64-bit) Macbook Pro


You're using a 32 bit kernel: On a 32 bit kernel each process can only address 4 GiB of memory, regardless of the amount of memory on the system. IIRC, this 4 GiB is broken up into 3 GiB of user memory and 1 GiB of kernel memory. So you're running into problems beyond 2.7 GiB because of that per-process 3 GiB user memory limit, and while I'm not sure exactly why you're running out at 2.7 instead of 3, it probably has to do with some sort of overhead.

So basically you need to switch to 64-bit if you need any more memory per process. You may be able to edge that 2.7 GiB up a bit, but 3 is going to be the absolute limit.

---

### Post by johnl on 2011-05-02
I would second trying to use mmap instead of malloc.

Also check your resource limits to make sure you aren't bumping into them ( ulimit -m from the shell or via getrlimit() )

I was able to map 8 gigs of memory on my 64-bit system which has only 3 gigs of memory, which resulted in some terrible swapping.  On a 32-bit system you'll only be able to  map less than 4G in one call since size_t is a 32-bit value.


Here's an example:

```

#include <stdlib.h>
#include <stdio.h>
#include <memory.h>
#include <sys/mman.h>
#include <sys/types.h>
#include <fcntl.h>
#include <unistd.h>

int main(int argc, char* argv[]) 
{
    if (argc != 2) {
        fprintf(stderr, "usage: %s <num-gigs>\n", argv[0]);
        return 1;
    }
    
    const static size_t gig = (1024 * 1024 * 1024);
    float  num  = atof(argv[1]);
    /* on a 32-bit system this will overflow at 4 gigs */
    size_t total = gig * num;

    /* an anonymous mapping has no backing file, so
     * ignore the fd and offset arguments */
    void* ptr = mmap(NULL, total, PROT_READ | PROT_WRITE,
                     MAP_ANONYMOUS | MAP_PRIVATE, -1, 0);
    
    if (ptr == MAP_FAILED) {
        perror("mmap");
        return -1;
    }

    printf("allocated %.02f GB at %p\n", num, ptr);
    printf("filling...\n");

    /* this will take a while if we start swapping */
    memset(ptr, 0x3C, total);

    printf("done.\n");
    
    munmap(ptr, total);
    return 0;
}

```

---

