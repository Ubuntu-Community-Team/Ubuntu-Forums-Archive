---
title: "What is Linux's page size on 64bit?"
date: 2008-05-10
forum: Programming Talk
---

### Post by LGS on 2008-05-10
I'm having a performance problem with a program that I'm running under Vista.  If Linux has a better solution, I'd like to try running it there.

I'll spare you the (pages of) details.  In summary, Vista (like XP) uses 4k pages when allocating memory.  When you allocate a lot of memory (like 2 gig), the table that the kernel uses to map between an application's address space and the physical memory becomes too large (~500,000 entries) to fit in the processor's cache (holds < 200 entries).  This results in serious performance hits, depending on how you use the memory.

Tests show that if my app could use larger pages (like 2Meg), I could reduce that table to <1000 entries and get an almost 25% increase in performance.  Vista's solution to this (MEM_LARGE_PAGES) is virtually unusable.  So I thought I'd check into Linux's.

What size pages does Linux use on 64bit processors?

---

### Post by smartbei on 2008-05-10
Could you explain why large pages is unusable? It seems to be the straightforward solution for this problem. As for the page size, see [this]("http://linux.die.net/man/2/getpagesize").

---

### Post by samjh on 2008-05-10
Use this program to determine what page size your system uses:

```
#include <unistd.h>
#include <stdio.h>

int main()
{
	int pageSize = getpagesize();
	
	printf("Page size on your system = %i bytes\n", pageSize);
	
	return 0;
}
```

On my Intel Core2 Duo 64-bit system, the page size is 4kB, which is normal for almost every desktop PC architectures.

Linux kernel 2.6.x versions support large pages (4MB).

Take a look at: [http://linux-mm.org/HugePages](http://linux-mm.org/HugePages)

---

### Post by stroyan on 2008-05-10
There is a processor dependent limit on the number of TLB entries
that support large pages.  You can use the cpuid or x86info package to
see what those limits are on x86 family CPUs.  It is quite possible that
the small number of TLB entries for huge pages will cause your program to
have more TLB misses than it has with tiny 4K pages and the full TLB.

There is a libhugetlbfs library that assists with using large pages
in linux.  See [http://sourceforge.net/projects/libhugetlbfs](http://sourceforge.net/projects/libhugetlbfs)

---

### Post by LGS on 2008-05-10
Thanks for the reply.

I'm not sure how much detail you are looking for about why VirtualAlloc(MEM_LARGE_PAGES) doesn't work.  After all, this isn't a Vista/Windows forum.

So, I'll hit some of the highlights, and if you are still interested, feel free to ask for more detail.

Programmatically, it isn't very difficult to implement.  There is a page ([http://msdn.microsoft.com/en-us/library/aa366720(VS.85).aspx](http://msdn.microsoft.com/en-us/library/aa366720(VS.85).aspx)) that describes the steps pretty well, leaving off only 1 critical step.

Unfortunately, there are several problems with the approach MS has taken:

1) My application is trying to allocate 1.9 gig on a 2 gig system.  Using 4k pages, the program is able to allocate that memory and will (after startup) run with zero page faults.

When using large pages, I can't even allocate half that much (apparently due to fragmentation).  And then only if I do the allocation within moments of startup.  Soon after that, the memory available for large pages drops fairly quickly to zero.

2) Also, Vista locks those pages in memory.  This has several consequences:

a) Two applications (or two instances of the same application) are not going to be able allocate any significant percentage of available RAM.  Although in theory, Vista can swap out entire apps to access locked pages, that's just not going to be practical with 1 gig apps.

b) The total amount of memory that can be allocated will have to be less than the physical memory of the computer (probably much less).

c) Security policy must be changed for every user that wants to be able to run apps that use large pages.

All-in-all, not a great solution for my needs, and probably a non-starter for any commercial app.

---

### Post by LGS on 2008-05-10
I don't have the dev environment set up on my ubuntu, so I don't have an easy way to run this.  Thanks for the numbers.

That link you provided looks very promising.  Sounds like this might be worth pursuing.

Is ubuntu a good place to start dev work?  Looks more like a family-friendly version of linux than a dev environment.

---

### Post by LGS on 2008-05-10
Yes, I've looked at the differences between entries for 4k and 2m pages.  Based on the docs I can find, my AMD processor allows 

L1: 32 * 4k pages (128K)
    or
    8 * 2M pages (~8M)

L2: 512 * 4k pages (2048K)
    or
    (2M data not provided, but probably > 1)

All-in-all, looks like a net win.  That along with some actual tests run using large pages and my specific app...

A good point tho, and thanks for mentioning it.  I'm still rather new to large pages.

---

### Post by stroyan on 2008-05-11
The linux hugetlbfs implementation does a little better with large page allocation.
It allows you to reserve memory using sysctl near boot time so
it will remain available for large pages without being spoiled by fragmentation.
But you do need to commit that RAM early or it will become
unavailable much the same way as it happens in windows.

The linux implementation does lock large pages in RAM.
Programs can't page in and out large pages to swap.

The only place I have seen particularly practical implementation of large
pages is in proprietary Unix systems like HP-UX.  That OS allows executables and
shared libraries to be tagged for large page use on text and data areas.
The tagging doesn't require any special privilege.  Preferred page sizes can
be set to a large range of values for different segments.  Those pages can
be swapped in and out.  And page size will gracefully degrade to smaller
sizes to handle alignment requirements and fragmentation of memory.
But... you have to run a proprietary OS on a different architecture such
as PA-RISC or Itanium.

---

### Post by LGS on 2008-05-12
For my current purposes, reserving the memory at startup may prove to be sufficient.  We'll see.  Right now I'm just trying to get the thing to compile using g++.  It's a console app, so I'm hoping it won't be TOO difficult.

By contrast, Vista takes the (reasonable) position that "free" memory is wasted memory.  Their new SuperFetch technology is designed to ensure that memory is always in use.  A sensible plan... unless you are worried about fragmentation.  Kind of a non-starter for me.

Eventually, MS (and Linux) are going to need to find a better solution.  As the "Rice" paper points out: "Relative TLB coverage is seen to be decreasing by roughly a factor of 100 over ten years."  And that was 6 years ago.  What's more, this paper doesn't seem to take into account the impact of multiple core machines.

I have to believe that dual core is making things even worse.  At one time processes were going to be swapping in and out of "the" processor and the TLBs would all be invalidated anyway.  With dual core becoming the standard, and 6 core on the horizon, it seems like the very idea of locality is disappearing.

I wonder why there isn't more hue and cry about Window's broken large pages?  At least if people are complaining about it, google ain't finding it for me.

---

### Post by LGS on 2008-05-17
Me again.  I need a bit more help, please.

So, I've got my app compiled and running under Ubuntu.  I have installed and compiled the libhugetlbfs project from sourceforge.  However, something is missing.

Apparently libhugetlbfs doesn't actually provide support for large (huge) pages.  It merely makes it easier to access the huge page support that is already in the OS.

But it appears that ubuntu doesn't have support for huge pages compiled in?  Is there some way to add that support without re-compiling the entire kernel/os?  Is there a build of linux (Fedora?  Linspire?) that has huge page support already built in?

---

### Post by stroyan on 2008-05-18
You will need to compile your own kernel to enable hugetlb.
Recompiling the kernel isn't so terrible.
You can follow the guide at [http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way](http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way)
I just went through that page and it seems to match ubuntu 8.04, other
than the specific kernel version number.
(Watch out for the subtle cd into /usr/src/linux before running make-kpkg.)
I did notice that they suggest 'make xconfig' but don't mention that you
need to 'sudo apt-get install libqt3-mt-dev' before you can do that.
You can just copy /boot/config-$(uname -r) to /usr/src/linux/.config and
then edit it to change
# CONFIG_HUGETLBFS is not set
# CONFIG_HUGETLB_PAGE is not set
to
CONFIG_HUGETLBFS=y
CONFIG_HUGETLB_PAGE=y
so you have the same kernel configuration except for the addition of huge pages.

---

### Post by LGS on 2008-05-18
Thanks for the pointers.  You have just turned an impossible task into a merely improbably one.  We'll see what happens.

If I had a better understanding of what I was doing, I would think about making a HOWTO page for all this.  Trying linux to see if its large pages will make my app run better is turning into quite the project.  An end-to-end guide of how to set this up would sure have helped me.

Still, if I get the perf boost I expect, it will all be worth it.

---

### Post by JosiahLuscher on 2012-03-03
Re: samjh's getpagesize.c program - which is excellent and effective... however.

Might be a bit easier to just:

*getconf PAGESIZE*

or

*getconf PAGE_SIZE*

---

