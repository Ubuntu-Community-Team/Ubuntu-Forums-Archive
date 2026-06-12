---
title: "controlling malloc allocation size"
date: 2013-07-04
forum: Programming Talk
---

### Post by allynm on 2013-07-04
Hello everyone,

Is there a technique for controlling the actual allocation size from the heap using malloc()?  I find that if I allocate a block of nominal size n bytes by calling malloc(n), the sys actually allocates much more, some of it "used", much more of it "not used".  If I want to trim the not used bytes there is a command that will do this post facto.  The smallest sized allocation then becomes just a single page (4096 bytes).  In many cases this would be more than ample to handle a dynamic buffer and not generate a segmentation fault.  

It would be nice to be able to control the behavior of malloc() so that it allocates no more than the number of bytes requested in the parameter.  Is there a way to do this?

Thanks,
Mark Allyn

---

### Post by dazman19 on 2013-07-04
Of my somewhat limited c/c++ experience, My understanding is that malloc(n) returns a pointer to the heap memory it allocated, or a null pointer if it fails. This returned pointer doesnt have a type, its actually of void type so you need to cast it then initialize.
int x = 50;
char * buffer;
buffer = (char*) malloc (x);

It might be nice to make your own wrapper function for malloc so you get back types you desire. 

If malloc is using more memory than x then i would assume this managed by the system itself but is not of any concern to your application.

---

### Post by allynm on 2013-07-04
Hi Jaunty,

I take your point that the system is managing the unused bytes and there is no particular reason to concern oneself with what is done with them.  However, if for some reason you write into the buffer more than it was designed (allocated) to hold, there is no way to know you have done so because as long as you don't exceed the total size (used + unused) you will note generate a seg fault.

Regards,
Mark

---

### Post by dwhitney67 on 2013-07-04
> **allynm said:**
> Hi Jaunty,

I take your point that the system is managing the unused bytes and there is no particular reason to concern oneself with what is done with them.  However, if for some reason you write into the buffer more than it was designed (allocated) to hold, there is no way to know you have done so because as long as you don't exceed the total size (used + unused) you will note generate a seg fault.

Regards,
Mark

Unfortunately, the action of overwriting a buffer does not generate a Segmentation Violation.  If you happen to overwrite a buffer and trample on some data that your program expects to use at a later time, then this would probably lead to a Segmentation Violation.  This is why troubleshooting these types of problems can be tricky.

Here's a crude example that demonstrates how a program continues running:
```

#include <stdlib.h>
#include <string.h>
#include <stdio.h>

int main()
{
    char* ptr1 = malloc(10);
    char* ptr2 = malloc(10);

    printf("ptr1 is pointing to: %p\n", ptr1);
    printf("ptr2 is pointing to: %p\n", ptr2);

    strcpy(ptr2, "Hello World\n");

    memset(ptr1, 'J', ptr2-ptr1 + 1);    // overwrite buffer with 'J' chars

    printf("data at ptr2 is: %s\n", ptr2);

    // These are commented out because a SegFault will occur once called.
    //free(ptr1);
    //free(ptr2);

    return 0;
}

```

Btw, with newer compilers, there is no need to cast the return value of malloc() as dazman19 indicated.

---

### Post by allynm on 2013-07-04
Hi Dazman19,

I have no idea why I gave you the name "Jaunty".  Sorry to call you by a ubuntu version name....

Mark

---

### Post by allynm on 2013-07-04
Hi dwhitney67,

Thanks for the very nice demo.  I haven't run it yet, but I will.  With a debugger as well.

Perhaps you can clarify a point that I find confusing about malloc().  When called it not only allocates a set of bytes and designates them "used".  It also generates addtional bytes that are "unused", and as my original post indicted, there is no apparent way I have yet found to conrol the number of "unused" (but apprently, "allocated") bytes.  This can be shown easily by a calling mallino() and examining the mallinfo struct it returns.

My original concern was the status of these "unused" bytes.  If I write into them (and I most certainly can), then is it possible for me to overwrite already written-to bytes.  If so, then in what sense are they "unused".  If not, then why are they "allocated unused"?  In other words, do I care if I write into the unused blocks out of negligence, or whatever?

Thanks for your help.

Mark

---

### Post by trent.josephsen on 2013-07-04
From memory, don't quote me on the details, but this is the general principle:

Requesting new memory from the operating system is expensive. malloc() does not request new memory from the OS every time you call it because that would incur an unacceptable performance penalty for many applications. Instead, it requests a large chunk of memory all at once and manages it internally. As a result, when you call free() on a pointer, that memory is not released to the OS immediately, but just goes into a list of free blocks that can be returned by a subsequent call to malloc(). All this is done by your process, not by the OS.

The memory you see as "unused" is not unused in the sense that other processes may use it -- it's reserved for your process. It's unused because your process isn't using it. But the "used" blocks aren't necessarily contiguous and don't have to appear in any particular order. You may write to such "unused" memory without causing a segfault, but malloc() won't mark it as "used", so a future call to malloc() could return a pointer that points into the middle of the formerly-unused memory. Then you would be in trouble.

Hope this is clear as mud.

---

### Post by dazman19 on 2013-07-04
> **allynm said:**
> Hi Dazman19,

I have no idea why I gave you the name "Jaunty".  Sorry to call you by a ubuntu version name....

Mark

No Worries

dwhitney67 yeh I have not used C/C++ for a while but its good to know the newer versions of c compilers are easier to use.

---

### Post by allynm on 2013-07-05
Good morning, trent.josephson,

After a call to malloc, a new membory break is established at the end of the "used" and "unused" allocated blocks, as I expect you know.  The only way I know to generate a seg fault is to attempt to write beyond the new break.  As long as you don't exceed the break you will not generate a seg fault.  

But, here's the deal.  If I allocate room for 10 ints using:

int * ptr=malloc(10*sizeof(int))

I will obtain 40 bytes of "used" heap and almost 135000 bytes of "unused, but allocated" heap.  I seem to have no ex ante ability to limit the amount of "unused" memory.  This seems wierd to me.  Why all this unused allocation?  What purpose does it serve?

Thanks for jumping into this trhead.

Mark

---

### Post by dwhitney67 on 2013-07-05
> **allynm said:**
> 
But, here's the deal.  If I allocate room for 10 ints using:

int * ptr=malloc(10*sizeof(int))

I will obtain 40 bytes of "used" heap and almost 135000 bytes of "unused, but allocated" heap.  


How did you get the number 135000?

---

### Post by allynm on 2013-07-05
good morning, dwihitney67,

I got it by running mallinfo() (defined malloc.h) to get a copy of the mallinfo struct.  There is a member in this struct called mallifo.fordblks that contains the number of unused but allocated blocks.  Perhaps I am misinterpreting events?  It's certainly been known to happen.

Thanks,
Mark

---

### Post by allynm on 2013-07-05
dwhitney67,

I got it by calling mallinfo().  This returns a mallinfo struct.  The struct member named fordblks supposedly reports the number of unused but allocated bytes.

Mark

---

### Post by dwhitney67 on 2013-07-05
> **allynm said:**
> I seem to have no ex ante ability to limit the amount of "unused" memory.  This seems wierd to me.  Why all this unused allocation?  What purpose does it serve?


Sorry, but I've never used or heard of mallinfo(), until today.  I'm not sure if one can say that the 'fordblks' are "allocated" to the program.  I'm not sure why anyone would care one way or the other.

---

### Post by allynm on 2013-07-05
Hi dwhitney67,

I've spent quite a few hours now trying to find out what the heck is meant by "allocated but not used" and haven't had any luck.  It is possible to get rid of some or nearly all of the "allocated but unused bytes" by issuing a malloc_trim(pad) command, where pad is the number of bytes to retain.  If you set pad to zero it will cut the number of bytes down to 1 page (4096 bytes). Still, for a short buffer this would leave behind a residuum of "allocated but unused" bytes.  This sets the brk at the page boundary, and if you try to write more than 4096 bytes it will generate a seg fault as it should.

I don't get it.  This malloc stuff seems not to be very well documented, even in the GNU glibc docs.

Thanks for pitching in.

Mark

---

### Post by dwhitney67 on 2013-07-05
What motivates you to even want to attempt this effort?

When analyzing how much data an application has allocated, not once in my 22+ years of developing s/w has the term "allocated but unused" been a topic of discussion.  It's more helpful to know how much real memory an application has allocated, and a good tool to analyze this is 'valgrind'.

If your desire is to govern how much data can be written to an allocated buffer (and generate a fault should too much be written), then you might have to invent your own Memory Manager, and also implement your own functions that emulate memcpy(), memset(), strcpy(), etc.  This seems like an awful lot of work with not much pay-back.

---

### Post by allynm on 2013-07-05
hi dwhitney67,

I have time on my hands to investigate these oddities.  When I find the answers I invariably  feel better.

One of the related functions to mallinfo() is mallopt().  I can't seem to make this thing work...yet another oddity.  I have toyed with the idea of creating my own mem manager so that I really do understand how it works.  

Tell me more, please if you've the time, about Valgrind.  Heard of it, but don't know much about what it's good for.


Mark

---

### Post by trent.josephsen on 2013-07-05
The source of confusion here is that there are two meanings of "allocate".

malloc() is a part of the C standard library, not a service provided by the kernel. It uses lower-level functions to request memory from the OS, which it also manages internally. Memory that has been assigned to your process by the kernel, but not reserved for any particular data structure by your program, can quite reasonably be described as "allocated but unused".

---

### Post by Bachstelze on 2013-07-05
> **allynm said:**
> However, if for some reason you write into the buffer more than it was designed (allocated) to hold, there is no way to know you have done so because as long as you don't exceed the total size (used + unused) you will note generate a seg fault.

Actually, yes, there is. That's what tools like Valgrind are for.

---

### Post by allynm on 2013-07-06
good morning trent.josephson and Bachsteize,

That is a highly interersting conjecture.  How can it be tested?  Why would the kernel allocate unused space (besides that for the process image)?

As for overwriting a buffer, yes indeed, memchk (or its fancy version in Valgrind) wiill do the job,of checking for overwrites, but of course, it must be invoked for this checking to be done.  Nothing is automatic.  Is this axiomatic?

Regards to all,
Mark

---

### Post by MG&amp;TL on 2013-07-06
You may wish to look at the actual *malloc *[source code]("http://code.metager.de/source/xref/gnu/glibc/malloc/malloc.c"). It's a huge file, (5000 lines) but most of it is comments which explain the general algorithm for various parts.

---

### Post by allynm on 2013-07-06
Good morning, MG&TL,

Good idea.  Thanks for the link.  I couldn't get hold of my copy of K&R--it's buried under hay in my barn.  

Mark

---

### Post by trent.josephsen on 2013-07-06
> **allynm said:**
> Why would the kernel allocate unused space (besides that for the process image)?

Because the process requested it.

Again, requesting memory from the OS is an expensive operation. The C standard library, presumably glibc most of the time, is written for good performance in typical use cases. It requests memory in large chunks to reduce overhead. Except for pathological cases, this is usually a good idea.

Imagine you were writing a program like sort that reads a file into memory line by line. You'd call malloc() and possibly realloc() many times for a great number of comparatively small buffers. If malloc() and free() trapped to the OS on every call, a 1000-line file would result in 2000 function calls and, potentially, 4000 context switches. That's hardly necessary. Allocating memory in pages of 4k bytes (which is typical, but not universal) results in significant speedup.[1] Does it waste memory? Depends on what you mean by "waste". 4 kilobytes is not a lot of RAM and RAM is cheap. Many programmers would consider 4 kilobytes an acceptable sacrifice to speed up a program like sort by 5%.[2]

[1] MMUs also operate on pages rather than individual bytes, so it's likely that you have to use pages of a certain size to take advantage of hardware memory management.
[2] No source for 5%; just a random number for illustrative purposes.

All that said, 135000 seems a little aggressive. Keep in mind, though, that defaults have to work reasonably well for almost everyone, so maybe it's a compromise between big-programs-acting-slow and small-programs-eating-memory. If you find out the reason for such a large initial size, I'd be interested to know.

You may also consider looking at [minix 3's libc](https://github.com/minix3/minix/blob/master/lib/libc/stdlib/malloc.c). It is a bit less complex than glibc but will still take some studying to work out.

---

### Post by allynm on 2013-07-08
Hi trent.josephson (and others),

Well, after spending a stupidly large amount of time--I finally admit it--yesterday I discovered what, I think, is going on and how to control the malloc'd size.  It turns out that when called, malloc automatically invokses mmap() and this is where the 135000 bytes is coming from.  This automatic invocation can be prevented by first calling mallopt(M_MMAP_THRESHOLD, size_t size).  If size_t size is 0 on up to the size of the amount of memory requested, mmap() will not be called and you get 1 page worth of memory to play with.  Once you exceed the size requested, for example, 10 ints's worth (40 bytes), mmap() will be called and you will get an addtional 135,000 + bytes.  The man page for mallopt() explains what happens in the usual rather cryptic fashion.

Cheers,
Mark

---

### Post by trent.josephsen on 2013-07-08
I didn't notice before that 135,000 == 128*1024 + 4096 until you mentioned it, but yeah, that makes sense... however, I'm still puzzled. If I'm reading the man pages correctly, malloc() shouldn't call mmap() unless you are trying to reserve at least M_MMAP_THRESHOLD bytes of memory **at once**, which cursory research indicates should be 128k... so 10 measly ints shouldn't ever cause that to happen.

Non-edit: I wrote a quick program that just displays the result of mallinfo(), calls malloc(), and displays mallinfo() again. Setting M_MMAP_THRESHOLD before malloc() doesn't affect the output. More interestingly, `hblks' stays at 0, so none of the memory represented by that 135whatever is mmap()ed.

I believe M_TOP_PAD is the parameter you want to change:
```
       M_TOP_PAD
              This parameter defines the amount  of  padding  to  employ  when
              calling  sbrk(2)  to modify the program break.  (The measurement
              unit for this parameter is bytes.)
<snip>
              Modifying M_TOP_PAD is a trade-off between increasing the number
              of system calls (when the parameter  is  set  low)  and  wasting
              unused  memory at the top of the heap (when the parameter is set
              high).

              The default value for this parameter is 128*1024.
```

---

### Post by allynm on 2013-07-09
good morning, trent.josephson,

Read your reply.  I must run off to the cardiologist at the moment.  Will return in an hour or so.  I want to test your M_TOP_PAD suggestion.  Interesting that so little about this subject shows up on the internet...

Cheers,
Mark

---

### Post by allynm on 2013-07-09
hello trent.josephson,

OK, here is a little proggy that sets TOP_PAD to zero.  The malloc stats call gives a brief display of what's mapped.  You invoke the thing on the command line with ./nualloc 1.  The 1 value is supposed to control the mallopt CHECK ACTION which supposedly provides some error checking on the memory allocation.  It fails to detect the out-of-bounds writing into p[49].  Don't know why it doesn't work.  But, it appears as if you are correct that TOP_PAD is what to set.  You still wind up mapping a full page...but hey who cares?

#include <malloc.h>
#include <stdio.h>
#include <errno.h>
#include <stdlib.h>

int main ( int argc, char * argv[] ){
int ret;
int * ptr = NULL;
if (argc > 1) {
if(mallopt(M_CHECK_ACTION, atoi(argv[1])) != 1)
{
    fprintf(stderr, "mallopt failed");
    exit(EXIT_FAILURE);
    }
}
mallopt(M_TOP_PAD, 0);
ptr = malloc(10*sizeof(int));
if (ptr==NULL) {
    fprintf(stderr, "malloc failed");
    exit(EXIT_FAILURE);
    }
malloc_stats();
ptr[49]= 32;
free(ptr);
//free(ptr);
return 0;
}

Mark

---

### Post by MG&amp;TL on 2013-07-09
A suggestion: have you tried running the program *strace* over your program, to see what your program is requesting in terms of system calls? Obviously there's a lot of noise to begin with, performing runtime startup tasks.

---

### Post by allynm on 2013-07-09
Hi MG&TL,

OK, good idea.  Here's a copy of strace ./nualloc 1 output:

mark@mark-HP-ProBook-4525s:~/asm$ strace ./nualloc 1
execve("./nualloc", ["./nualloc", "1"], [/* 38 vars */]) = 0
brk(0)                                  = 0x9823000mark@mark-HP-ProBook-4525s:~/asm$ strace ./nualloc 1
execve("./nualloc", ["./nualloc", "1"], [/* 38 vars */]) = 0
brk(0)                                  = 0x9823000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb779d000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=107921, ...}) = 0
mmap2(NULL, 107921, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7782000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\226\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1730024, ...}) = 0
mmap2(NULL, 1739484, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb75d9000
mmap2(0xb777c000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1a3) = 0xb777c000
mmap2(0xb777f000, 10972, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb777f000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb75d8000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb75d8900, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb777c000, 8192, PROT_READ)   = 0
mprotect(0x8049000, 4096, PROT_READ)    = 0
mprotect(0xb77c0000, 4096, PROT_READ)   = 0
munmap(0xb7782000, 107921)              = 0
brk(0)                                  = 0x9823000
brk(0x9824000)                          = 0x9824000
write(2, "Arena 0:\n", 9Arena 0:
)               = 9
write(2, "system bytes     =       4096\n", 30system bytes     =       4096
) = 30
write(2, "in use bytes     =         48\n", 30in use bytes     =         48
) = 30
write(2, "Total (incl. mmap):\n", 20Total (incl. mmap):
)   = 20
write(2, "system bytes     =       4096\n", 30system bytes     =       4096
) = 30
write(2, "in use bytes     =         48\n", 30in use bytes     =         48
) = 30
write(2, "max mmap regions =          0\n", 30max mmap regions =          0
) = 30
write(2, "max mmap bytes   =          0\n", 30max mmap bytes   =          0
) = 30
exit_group(0)                           = ?
mark@mark-HP-ProBook-4525s:~/asm$ 

access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb779d000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=107921, ...}) = 0
mmap2(NULL, 107921, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7782000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\226\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1730024, ...}) = 0
mmap2(NULL, 1739484, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb75d9000
mmap2(0xb777c000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1a3) = 0xb777c000
mmap2(0xb777f000, 10972, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb777f000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb75d8000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb75d8900, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb777c000, 8192, PROT_READ)   = 0
mprotect(0x8049000, 4096, PROT_READ)    = 0
mprotect(0xb77c0000, 4096, PROT_READ)   = 0
munmap(0xb7782000, 107921)              = 0
brk(0)                                  = 0x9823000
brk(0x9824000)                          = 0x9824000
write(2, "Arena 0:\n", 9Arena 0:
)               = 9
write(2, "system bytes     =       4096\n", 30system bytes     =       4096
) = 30
write(2, "in use bytes     =         48\n", 30in use bytes     =         48
) = 30
write(2, "Total (incl. mmap):\n", 20Total (incl. mmap):
)   = 20
write(2, "system bytes     =       4096\n", 30system bytes     =       4096
) = 30
write(2, "in use bytes     =         48\n", 30in use bytes     =         48
) = 30
write(2, "max mmap regions =          0\n", 30max mmap regions =          0
) = 30
write(2, "max mmap bytes   =          0\n", 30max mmap bytes   =          0
) = 30
exit_group(0)                           = ?
mark@mark-HP-ProBook-4525s:~/asm$ 

I am no expert in reading straces but they seem to indicate mmap is being called extensively even though a mere,, measly 10 ints are being allocated.  What do you make of it?  Any in terpretive comments would be most appreciated.

Cheers,
Mark

---

### Post by allynm on 2013-07-09
Hi MG&TL

Somehow the printout from strace was duplicated in my prior response.  You may disreegard everything that follows the first reference to exit_group(0).  Sorry.

Mark Allyn

---

### Post by MG&amp;TL on 2013-07-09
> ```
mprotect(0xb777c000, 8192, PROT_READ)   = 0
mprotect(0x8049000, 4096, PROT_READ)    = 0
mprotect(0xb77c0000, 4096, PROT_READ)   = 0
munmap(0xb7782000, 107921)              = 0
brk(0)                                  = 0x9823000
brk(0x9824000)                          = 0x9824000
write(2, "Arena 0:\n", 9Arena 0:
)               = 9
write(2, "system bytes     =       4096\n", 30system bytes     =       4096
) = 30
write(2, "in use bytes     =         48\n", 30in use bytes     =         48
) = 30
write(2, "Total (incl. mmap):\n", 20Total (incl. mmap):
)   = 20
write(2, "system bytes     =       4096\n", 30system bytes     =       4096
) = 30
write(2, "in use bytes     =         48\n", 30in use bytes     =         48
) = 30
write(2, "max mmap regions =          0\n", 30max mmap regions =          0
) = 30
write(2, "max mmap bytes   =          0\n", 30max mmap bytes   =          0
) = 30
exit_group(0)                           = ?
```


That is probably the relevant parts (to my knowledge, *malloc* does not need to do any  *mprotect*ing, although I'm hardly an expert, or even close). You'd probably have to lookup the *brk* system call to work out how much is actually being created.

> **allynm said:**
> Hi MG&TL

Somehow the printout from strace was duplicated in my prior response.  You may disreegard everything that follows the first reference to exit_group(0).  Sorry.

Mark Allyn

Just FYI, you know there's an edit post button, right? :)

---

### Post by allynm on 2013-07-09
Hi MG&TL.

Here is the relevant secton of man btk:

 > [brk()  sets  the  end of the data segment to the value specified by addr, when that value is
       reasonable, the system has enough memory, and the process does not exceed its  maximum  data
       size (see setrlimit(2)).]

brk(0) [somewhat misleadingly] gives the current program break.

If you look at the two calls to brk you will see that they are exactly 4096d apart.  

As for the edit thing, well I forgot.  It's just that simple.  I'll try to be better in the future...:D

Cheers,
Mark

---

### Post by trent.josephsen on 2013-07-09
> **allynm said:**
> The 1 value is supposed to control the mallopt CHECK ACTION which supposedly provides some error checking on the memory allocation. It fails to detect the out-of-bounds writing into p[49].
You may want to re-read the section about M_CHECK_ACTION. It does not change what error checking is done, just what action is taken when an error is found. glibc can't tell if you're doing funny stuff with the memory it gives you; glibc doesn't own the memory or get notified when it's used. That means the kernel would have to do it -- but how could the kernel know which parts of memory glibc had allocated "for use" and which were part of the free list? Long story short, glibc's internal checking checks its own algorithms and may notice if you are using them incorrectly (the example the manpage gives is calling free() twice), but it won't check that you're doing anything sensible with the memory. That would be like me giving you a pad of paper to take notes on and then hanging around indefinitely to make sure you didn't write outside of the lines.

> You still wind up mapping a full page...but hey who cares?

Not sure what else you were expecting, since pages are no more nor less than the fundamental unit of memory mapping. Mapping less than a page would be like addressing part of a byte. Furthermore, paging is done in hardware on modern systems, so you couldn't get less than a page if you wanted to. (Well, I guess you could segment memory in software at the kernel level.)

If you want to find out whether a program overflows its buffers, the surest way is to replace every appearance of gets(), sprintf(), strcat(), strcpy() and other such functions with their bounds-checking counterparts, remove every appearance of (s)scanf() with plain "%s" in the format string, and then verify every remaining assignment/function call by inspection. Valgrind is a close second, but it won't catch every possible error, so don't assume no valgrind messages = no memory-related bugs.

Edit: BTW, as to the mmap2()s you see in the strace output, I think a little printf-debugging will show you that those are also glibc's doing (or the kernel itself) and have nothing to do with whether malloc() ever gets called.

---

### Post by allynm on 2013-07-10
Good morning trent.josephson,

I had read the section on M_CHECK_ACTION a number of times.  What I discovered is that it will notify if you call free() more than once, but not if you overwrite a memory allocation.  The man page on this parameter does not disclose what it will -- or can -- check so I had come to the wrong conclusion that I wasn't using it correctly to find overwriting.  Now I know.

You write:

> You may want to re-read the section about M_CHECK_ACTION. It does not  change what error checking is done, just what action is taken when an  error is found. glibc can't tell if you're doing funny stuff with the  memory it gives you; glibc doesn't own the memory or get notified when  it's used. That means the kernel would have to do it -- but how could  the kernel know which parts of memory glibc had allocated "for use" and  which were part of the free list? 

This clarifies a fundamental misconception I had about the units allocated.  I actually had thought that they could be as small as 1 byte within a page.  But, it actually isn't obvious (however true it obviously is) that the kernel CAN'T know which parts of memory glibc had allocated "'for use'"...  You will no doubt say that this betrays my ignorance of the ABI and how it works and you would be right.  So, how does it work?

As for the mmap(2) calls, I had reached the same conclusion you did.  I'll try your printf method and see what turns up.

Thanks for your help on this.

Cheers,
Mark

---

### Post by trent.josephsen on 2013-07-11
Just want you to know I can't answer right now for reasons of time, but I haven't forgotten the thread and I'll come back to it w/in the next few days.

---

### Post by trent.josephsen on 2013-07-11
(sorry for double post -- UF wasn't responding and I couldn't tell if it accepted my first one)

---

### Post by allynm on 2013-07-11
Good morning, trent.josephsen,

I realized suddenly that mmap and malloc do very different things.  I think I understand what malloc does, at least in principle,  but I certainly don't understand what mmap does.  Where the heck is it "mapping" to (bad grammar).

At any rate, I will be looking forward to hearing more from you.  

Thanks,
Mark Allyn

---

### Post by trent.josephsen on 2013-07-13
Well, you asked for it. Expect to take an hour to read and understand this post unless you already know most of it.

Disclaimer: I am not an expert, this is not my specific area of expertise, blah blah blah. When I speak in vague generalities, it's because I don't know something and I'm trying to avoid giving you the wrong idea. I'm going to give some context to this before I address (tee hee) your actual question, so feel free to skip stuff you already know.

Back in the day, memory was simple. Let's say you're using the original [m68k (wikipedia)](https://en.wikipedia.org/wiki/Motorola_68000), which has 24 external address lines and therefore, without the use of any external memory management or other trickery, can address 16 MB of memory. There is a one-to-one correlation between addresses used in your program and physical memory addresses; if you issue an instruction to read memory location 0x123456, the processor puts 0x123456 on the address bus.

This is fine for some simple projects like arcade games or printers, but it has some major drawbacks for general-purpose computing. For starters, any code running on the CPU can access the entire address space -- which makes it easy for any process to accidentally (or intentionally) scribble on memory that belongs to other processes or the OS itself. It also limits your total memory to the amount of memory physically connected to your CPU that can be addressed at one time.

The solution to these and many other problems, as you may already know, is [virtual memory](https://en.wikipedia.org/wiki/Virtual_memory). If you're from a Windows background you may think of virtual memory as just "swap", but it goes beyond that; virtual memory lets you access non-contiguous blocks of memory as if they were contiguous, permits mapping virtual memory addresses to components that don't have "addresses" per se (like disks and I/O devices) and can be used to segregate processes into their own "spaces" with mutually independent addressing schemes. In general, virtual memory makes things lots easier for everybody (except the EEs who are designing the chips). Motorola's 68010 was a successor to the 68000 that could support virtual memory, although it did not have an internal memory management unit.

Virtual memory works by having the MMU, which is a hardware component and today almost always part of the processor, translate virtual memory addresses to physical addresses (or disk accesses, etc.) at run time. [Paging](https://en.wikipedia.org/wiki/Paging) is the memory management method most essential to modern computing. With paged memory, when your process tries to access memory location 0x123456, that address is split into a *virtual page number* and a *page offset*. If we assume 4096-word pages, the page offset needs to be 12 bits, so for our example the page offset is 0x456 and the virtual page number is 0x123.[1] The memory management unit looks up the **virtual** page number in the *page table* to find out what **physical** page it corresponds to.

N.B. If the physical page is somewhere on a hard disk and not in main memory (aka a page fault), then the CPU has to swap it in, which can take millions of cycles as opposed to a few dozen cycles for RAM (or one or two cycles for cache). Pages are made large (4k or bigger) in part to minimize the performance penalty of swapping, since larger pages fragment less and decrease the frequency of page faults. This is why you can't map less than 4096 bytes; 4k is a compromise value chosen by the hardware designers.

Each process has its own page table. When you switch from one process to another (multitasking), the MMU uses different page tables to map virtual addresses to physical addresses. Address 0x123456 for one process isn't the same location as address 0x123456 for another process, even if they're both loaded into main memory at the same time, because the page number 0x123 maps to different things in the two different page tables. The page table for your process is saved when your process is suspended and restored when it resumes. A process can't access something that isn't in its page table, and so the individual processes are isolated from each other by virtue of their different page tables.

As for mmap() and sbrk(). The operating system (obviously) is the initial "owner" of all the memory available to the system, and the process manager and/or memory manager is the part of the OS that leases ("allocates") memory to the various processes under its control. To take advantage of the hardware, the OS almost always uses page sizes of the same size as the MMU.[2] In Linux, mmap() and sbrk() are actually wrapper functions for the mmap2 and brk system calls that trap to the OS. I don't truly understand what the difference really is between them, and I imagine you would need to do some hardcore source diving to truly answer that question. (I'm sure hysterical raisins are at the bottom of it, somehow.)

One way or the other, the kernel can give your process more pages when asked to by one of these system calls. Simplistically, if I wrote a program that called brk(), I would expect the kernel to add (at least) one page to my process's page table, just after the last entry for the heap. That way, if I had already somehow had a pointer that pointed to the end of the heap, I could increment it by one and it would be pointing to the first address on the next page. With our 24 bit address analogy, if the top of my heap is (virtual) 123FFF and I call brk() (the system call), it would find a new page somewhere, maybe at physical address 777000, and store the value 777000 in my page table at location 124. Then when I increment 123FFF to 124000, and dereference it, 124000 gets mapped to 777000 and I move on instead of causing a segfault.

<highly speculative>
I think "segmentation fault" may actually be a misnomer here. A segmentation fault would be like trying to write to physical address 777000 when that address is part of my own address space, but in fact belongs to another process or is read-only. I suspect it's actually the case that the virtual address can't be looked up in the page table or is flagged as "unused", which would make it a kind of page fault. But segmentation faults are what we're all used to calling it.
</highly speculative>

malloc() is different. If getting a page from the kernel is like leasing a storage space, using malloc() is like sectioning it off: chairs in this corner, lamp in this corner, couch along this wall, books sitting on a pallet over here.[3] The guy who owns the storage facility (the kernel) isn't going to care where you store what, as long as you don't start knocking holes in the walls to gain access to other peoples' space (other processes' memory). malloc is not a system call; it's part of the C standard library and it runs as part of your process. Just like you could write your own sprintf(), you could also write your own malloc() and manage memory any way you wanted to, using the same system calls.[4]

I hope I'm making it clear that there's nothing special about the function malloc() except that the C standard specifies it exists. Since that's true, and since it's the *only* portable (i.e. C standard) way to obtain dynamically allocated memory, any successful implementation of it has to make compromises for good performance in the average case and acceptable performance in adverse circumstances. It seems that the writers of glibc chose to have it overallocate by 128k by default, but they knew that some people might want different behavior, so they provided mallopt() as a means of reaching inside malloc() with a screwdriver to twiddle the [trim pots](https://www.google.com/search?q=trim+pot).

I think I may have lost focus somewhat, so I'm leaving it here. Let me know if I am confusing you or if I missed the point entirely.

Notes:
[1] Just an example. I don't know of any real computer with only a 24 bit address space that uses half of those bits for pages.
[2] But Minix, for example, doesn't use paging at all.
[3] Never store books on the floor.
[4] K&R2 has an example implementation of malloc()/free() that uses sbrk() on pp.185-189. You might try compiling this and examining its memory consumption behavior.

References:
If you are really interested in this kind of thing, I do suggest getting books about it. I've had the second one for a long time but it never made a whole lot of sense until after I read the first one (which was a textbook I used in college, and is pretty well written.)
[LIST]
[*]Patterson, David A. and John L. Hennessy. *Computer Organization and Design: The Hardware/Software Interface*, 4th ed.
[*]Tanenbaum, Andrew S. and Albert S. Woodhull. *Operating Systems: Design and Implementation*, 3rd ed.
[*]Kernighan, Brian W. and Dennis M. Ritchie. *The C Programming Language*, 2nd ed.
[*]and, of course, Wikipedia
[/LIST]

---

### Post by allynm on 2013-07-16
Good morning,  trent.josephsen

Wanted to let you know that I am about one-third of the way thru your tutorial.  It is highly informative.  Until very recently (within the last year) I had paid no attention at all to how the OS (Windows or Linux, I've done both) did its business.  For some reason, perhaps connected with doing stuff in Linux, I developed more interest in how the system works than in writing programs.  Don't have a clue why.  Previously I had just been quite content to call API's and let it go at that.  Think maybe it had to do with getting curious about shared objects....

Anyway, whilst you were away I actually did code and run the malloc() in K&R (section 8.7).  It certainly works and it is very compact.  In the process of trying to use it I discovered there was a feature about char * charptr I didn't understand and it stymied me for two days until I discovered that to use it with malloc() one must use strcpy().... I also have gotten a copy of dlmalloc(), but not yet compiled it.  Also have used Valgrind and it has sort of become a standard for me.

I do not have the Tanenbaum et al. book, but do have the others and will of course (and to some extent have already) spend more time with them.  

My enormous thanks for taking the time to create the tutorial.  In my parasitical fashion, I am certain to be back with more questions...

Regards,
Mark

---

