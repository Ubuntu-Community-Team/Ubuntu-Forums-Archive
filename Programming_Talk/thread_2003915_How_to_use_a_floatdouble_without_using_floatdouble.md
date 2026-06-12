---
title: "How to use a float/double without using float/double keyword?"
date: 2012-06-14
forum: Programming Talk
---

### Post by geewhan on 2012-06-14
I know this is weird to ask, but how do you set a variable as a decimal without using the keywords float/double?

I ask this because when I am compiling the Kernel I get an error when I use float/double in the tcp_vegas.c file.

These are the errors I am getting, if anyone knows how to go around this please let me know. Though like I said it is because I was using the float/double keywords; I used u32 (unsigned 32) to replace the float/double which got rid of the errors.

```

ERROR: "__addsf3" [net/ipv4/tcp_vegas.ko] undefined
ERROR: "__fixunssfsi" [net/ipv4/tcp_vegas.ko] undefined
ERROR: "__mulsf3" [net/ipv4/tcp_vegas.ko] undefined
ERROR: "__muldf3" [net/ipv4/tcp_vegas.ko] undefined
ERROR: "__floatsisf" [net/ipv4/tcp_vegas.ko] undefined
ERROR: "__adddf3" [net/ipv4/tcp_vegas.ko] undefined
ERROR: "__fixunsdfsi" [net/ipv4/tcp_vegas.ko] undefined
ERROR: "__floatsidf" [net/ipv4/tcp_vegas.ko] undefined
ERROR: "__subsf3" [net/ipv4/tcp_vegas.ko] undefined

```

So is there an algorithm, function, or a way to do a float/double without using those keywords?
An example

float a = 3.145678; //I do not want this
(some algorithm/function)-> a = 3.145678654; //This is somewhat I want

I hope this makes sense, if it doesn't I will try to explain it better.

Thanks

---

### Post by Bachstelze on 2012-06-14
This is not at all clear, but whatever it is that you want to do, you probably Can't Do That&#8482;. I suggest that you learn C before even trying to hack the kernel.

---

