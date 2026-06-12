---
title: "Find out architecture bit"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by rockymaxsource on 2008-11-17
Hey,

I'm trying to install the flash plugin for my firefox(Mozilla Firefox 3.0.1). How do I find out I'm running 64-bit Hardy on an 64 bit processor or 32-bit Hardy on 32 bit processor?

Blessings,
Rocky

---

### Post by taurus on 2008-11-17
Applications -> Accessories -> Terminal
```
uname -a
```

---

### Post by gletob on 2008-11-17
Please post the output of typing into a terminal 
```
uname -a
```

EDIT: You wascally wabbit you beat me

---

### Post by rockymaxsource on 2008-11-17
Hey,

Thanks for your reply! The result is:

> rocky@rocky-laptop:~$ uname -a
Linux rocky-laptop 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux


---

### Post by taurus on 2008-11-17
> 
rocky@rocky-laptop:~$ uname -a
Linux rocky-laptop 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 **[COLOR="Blue"]i686[/COLOR]** GNU/Linux 


You are running 32bit.  Otherwise, you would have seen x86_64 if you are running 64bit.

---

### Post by oldos2er on 2008-11-17
"Linux rocky-laptop 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux"

 Your kernel is 32-bit, but that doesn't tell anything about whether your processor is 64-bit or not.

---

### Post by rockymaxsource on 2008-11-18
Hey,

> "Linux rocky-laptop 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux"

Your kernel is 32-bit, but that doesn't tell anything about whether your processor is 64-bit or not. 

Then, How can I find the information?

Blessings,
Rocky

---

### Post by hyper_ch on 2008-11-18
```

lshw

```
or
```

lshw -html > ~/Desktop/hardware.html

```
or
```

cat /proc/cpuinfo

```

---

### Post by rockymaxsource on 2008-11-18
Hey,

The attachment is the result for viewing /proc/cpuinfo.

Thanks!
Rocky

---

### Post by jamesrl on 2008-11-18
You have a core 2 duo, which is a 64 bit processor.  You happen to be running it as a 32-bit processor as you didn't select 64 bit ubuntu when you installed it.  Therefore, your options are to download and reinstall ubuntu as 64-bit mode or continue running in 32 bit mode (and install 32 bit flash).  

You probably won't see a big difference, unless you want to have more than 3.2 Gb of memory on your computer or do lots of calculations that involve 64 bit (double precision) floats and their pointers.

---

### Post by hyper_ch on 2008-11-18
now you only need to find out if your motherboard supports also 64bit...hence I posted first the lshw options.

---

### Post by rockymaxsource on 2008-11-18
Hey,

Attached is the result for lshw.

Blessings,
Rocky

---

### Post by jamesrl on 2008-11-18
**hyper_ch** can you clarify (or someone else)?  I've never heard of anyone saying you need to check if the motherboard is capable of running in 64 bit before.  I know you can have motherboards that won't support 64-bit CPUs like say the intel core 2, but if the motherboard can run with an intel core 2 (even in 32 bit mode) than it is able to support the CPU and can run in 64 bit mode.

I may be mistaken though ...

More on supported motherboards for Intel Core 2: [http://en.wikipedia.org/wiki/Intel_Core_2](http://en.wikipedia.org/wiki/Intel_Core_2) (though can't tell via lshw output what the motherboard is by product # 0TT354)
and a thread where someone seems to verify what I thought:
[http://ubuntuforums.org/showthread.php?t=722599](http://ubuntuforums.org/showthread.php?t=722599)

---

### Post by jamesrl on 2008-11-18
Also there's always just take [the 64 bit live cd]("http://www.ubuntu.com/getubuntu/download"), try it out if you are curious about 64 bit mode (if it works you know 64 bit is supported).  I am 99% certain that  your motherboard will support your 64 bit core 2 chip perfectly fine.  But don't expect that 64 bit to run double as fast or anything ... it just allows you to do 64 bit calculations faster and access more than 2^32 bits=4Gb of memory (which in practice is 3.2 Gb and some addresses are reserved).

---

### Post by 3rdalbum on 2008-11-18
Don't expect 64-bit to run faster at all. (I know, because I'm running it!)

If the motherboard can support a Core 2 Duo, I'm sure it can support it in 64-bit operation.

---

### Post by jamesrl on 2008-11-18
**3rdalbum**
I'll have to disagree with you, 64-bit ubuntu running certain tasks will work faster.  I don't notice any particular speed advantages/disadvantages for most programs like say firefox (also have never benchmarked or anything), but I do notice significant differences for scripts involving lots of 64 bit floating point calculations.

Running the same (python) script in 32 bit vs 64 bit ubuntu, I find 64 bit ubuntu works ~1.5 as fast.  The scripts deal extensively with large arrays of double-precision floats (via scipy), I find that my scripts are about finish in about 70% of the time they originally took in 64 bit ubuntu vs 32 bit ubuntu, running on the same computer with an Intel Core 2 Quad processor (2.4GHz Q6600 with no overclocking) [just one uses a partition mounted to / with 32 bit ubuntu that was originally installed by Dell, and one uses a partition mounted to / with 64 bit ubuntu installed by me].  

I should also mention that the 64-bit ubuntu installed by me is 8.10 vs 8.04 (though I significantly doubt that would have a major difference in python speeds), and also that the 64-bit speed might be slightly underestimated as my 64 bit install has full-disk hard drive encryption (so it should take slightly longer to load files).  And for the record it is not because I am 'maxing' out the 3.2 Gb vs 4.0 Gb of memory ... the script uses less than 1 Gb of memory (and I usually have only about 1.5 Gb of non-cached memory in use when the scripts are running).

EDIT: Just did test again: found script on x86-64: ran at 230s vs script on i686: ran 321s (43% improvement in speed; finished in 72% of the time)

---

