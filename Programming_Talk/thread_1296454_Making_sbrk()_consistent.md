---
title: "Making sbrk() consistent"
date: 2009-10-20
forum: Programming Talk
---

### Post by ajb2 on 2009-10-20
I'm finding that this program, running under Ubuntu, produces results that are all over the (memory) map:

main () {
   printf ("%08X\n", sbrk(0));
}

If I run the program several times, the results look they're produced by a random number generator:

086BE000
0850F000
08DC7000
099D5000
084DD000
097CB000

I get similar results if I use, say, malloc(10).

The problem is that, for the purposes of debugging an application that uses sbrk() or malloc(), it would be much better if the initial program break were consistent, so that if I have to display allocated addresses or set a debugger breakpoint when a certain pointer is set to a certain address, for instance, the addresses will be the same from one run to the next.

Is there anything I can do to, say, set the program break to a certain value at the beginning of the program, or fix things so that it returns consistent values?  Any help would be appreciated...

Thanks in advance...

---

### Post by johnl on 2009-10-20
There was just a thread about this.

[Address Space Layout Randomization](http://en.wikipedia.org/wiki/Address_space_layout_randomization) is the reason you see this result.  Without getting into whether or not this is a good idea, there is an option somewhere in /proc to turn this off; someone else will know exactly where.

---

### Post by Arndt on 2009-10-21
> **johnl said:**
> There was just a thread about this.

[Address Space Layout Randomization](http://en.wikipedia.org/wiki/Address_space_layout_randomization) is the reason you see this result.  Without getting into whether or not this is a good idea, there is an option somewhere in /proc to turn this off; someone else will know exactly where.

This thread: [http://ubuntuforums.org/showthread.php?t=1291856](http://ubuntuforums.org/showthread.php?t=1291856)

---

### Post by ajb2 on 2009-10-21
Thank you, John and Arndt; I tried the instructions in the referenced thread, and they worked.  

Interestingly, it appears that that thread was started by a compiler writer, which is exactly my situation also.

---

