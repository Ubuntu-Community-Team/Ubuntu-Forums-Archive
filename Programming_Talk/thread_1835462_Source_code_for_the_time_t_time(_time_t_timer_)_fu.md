---
title: "Source code for the time_t time( time_t *timer ) function"
date: 2011-08-29
forum: Programming Talk
---

### Post by devkota on 2011-08-29
More specifically, I am seeking to know how the clock ticks are read and then they are stored in the data structure. The time_t is at least 2 bytes long since they store somewhat unique timestamp(with all the year, month, day, hour, second, etc). 
I am trying to encode just 24 hours time with as less as possible number of bits. I am able to encode 86400 seconds by using 11 bits( as shown in the attached figure), Is it possible to do so by using lesser bits than 11? 
For that, I am trying to see how the time is calculated by using the clock ticks information by the standard C function time_t time( time_t *timer ) declared in time.h .
I searched the code for time.h in the ubuntu machine I could find many header files time.h which just declare the time() function with extern keyword. How can I locate the source file location where the actual implementation of the time() function is done. 

I am hoping for relevant guidance.

Thanks

---

### Post by dwhitney67 on 2011-08-29
The time() function merely returns the number of seconds since the Epoch (00:00:00 UTC, Jan 1, 1970).  The return type is a time_t, whose size is 4 bytes, but should not really matter.

You have the option of passing a pointer to a time_t variable to the time() function where the result will be stored.

Examples...
```

time_t theCurrentTime = time(NULL);

```
```

time_t theCurrentTime;

time(&theCurrentTime);

```

If my answer does not satisfy your needs, please clarify what exactly you require.

---

### Post by devkota on 2011-08-29
Hi dwhitney67,
Actually I am seeking for the algorithm that the time() function is using i.e. the way it reads the interrupt timer and calculates the number of seconds. I am longing more to learn about the SOURCE code of the time() function and I am not able to get it.

---

### Post by Bachstelze on 2011-08-29
The time() function just calls the time system call. On Linux, you can find the source code for it in arch/ARCH/kernel/time.c in the kernel source.

---

### Post by devkota on 2011-09-06
Dear Frens,

Thank you for your replies and helping me for understanding things.
Also, as I have said earlier in my description that 24 hours can be encoded by 11 bits, I had a calculation error and 11 bits can encode 24 hours not in terms of seconds but in terms of minutes only. For encoding 24 hours in terms of seconds (i.e. 86400 seconds) it requires at least 17 bits. I could not find ways to encode time(86400 seconds) in less than 17 bits.

Thank You

---

### Post by Bachstelze on 2011-09-06
Well if you want to encode 86400 different values, obviously you need A7 bits. There's no way to use less than that.

---

