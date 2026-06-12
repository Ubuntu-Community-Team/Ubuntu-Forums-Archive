---
title: "Tiny program maxes 4 CPU cores - WHY?"
date: 2009-03-16
forum: Programming Talk
---

### Post by Krupski on 2009-03-16
Hi all,

I was playing around with the time() function just to learn how it works. I made up a tiny program called "pause.c" that works, but when run it kicks all 4 cpus (Intel Core 2 Quad) up to full speed!!

What the heck?

Here's the code:

```

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main(int argc, char *argv[])
{
    long int time1, time2;
    int delay;

    // look for one command line param
    if(argc != 2) {
        fprintf(stderr, "usage: pause time (in milliseconds)\n");
        return 1;
    }

    // get desired delay
    delay = atoi(argv[1]);

    // get start time
    time2=time1=clock();

    // while end-start < desired...
    while((time2) - (time1) < (delay * (CLOCKS_PER_SEC / 1000))) {
        time2=clock();
    }

    return 0;
}

```

Here's a dump of the average of 4 cores while the pause program was running (1 sample per second, pause ran for 10 seconds):

```

 time    ghz
------  -----
000000, 1.596
000001, 1.596
000002, 1.729
000003, 1.596
000004, 1.729
000005, 1.596
000006, 1.596
000007, 1.596
000008, 1.729
000009, 1.596
000010, 2.660 <---- start
000011, 2.660 
000012, 2.660 
000013, 2.660 
000014, 2.660 
000015, 2.660 
000016, 2.660 
000017, 2.660 
000018, 2.660 
000019, 2.660 
000020, 2.660 <---- end
000021, 1.729
000022, 1.596
000023, 1.596
000024, 1.596
000025, 1.596
000026, 1.596
000027, 1.596

```


Anyone know why this uses all the CPU power?

Thanks!

-- Roger

---

### Post by mdawg414 on 2009-03-16
My guess would be because that loop is executing so frequently and maybe the scheduler cant determine what is actually going on so it doesnt know how to let other programs do work??? It's bascially setting time2=clock() as fast as it possibly can, which is using all 2.66GHz for you. This is just a guess though.

---

### Post by jimi_hendrix on 2009-03-16
throw in a sleep() down there

---

### Post by Npl on 2009-03-16
The while loop will max 1 CPU for sure, as it aggressively polls. Its better to give the CPU back to the system with **sleep** than polling like mad.

Also I think Core2 cant clock its cores independly, so if one Core needs to run at full frequency all others run at the same speed. Measuring load by the clock frequency is a bad idea anyway.

---

### Post by Krupski on 2009-03-16
> **Npl said:**
> Also I think Core2 cant clock its cores independly, so if one Core needs to run at full frequency all others run at the same speed. Measuring load by the clock frequency is a bad idea anyway.

I just ran a tiny program that samples all 4 cores once per second and records the data. Then I graphed it (see below). The task I did was to gunzip a 2 gigabyte file. The graph shows relative core speeds (I had to add offsets to the Y axis so each curve would show separately).

Core 0 is on top, then 1, 2 then finally 3 on the bottom. You will see that the cores can indeed be clocked separately.

BTW, the CPU is an Intel Core 2 Quad Q6700 running Ubuntu 8.10 64 bit OS and using the "acpi-cpufreq" controller and the "conservative" governor.

Here's the graph (click on the little one for a full size graph):


[CENTER][[img]http://home.roadrunner.com/~krupski/images/4-cores-thumb.jpg[/img]]("http://home.roadrunner.com/~krupski/images/4-cores.jpg")[/CENTER]

-- Roger

---

### Post by Krupski on 2009-03-16
> **jimi_hendrix said:**
> throw in a sleep() down there

I know about sleep(). I was trying to learn how time() worked and just figured I would make a time delay program with it to learn how it worked.

I was surprised to see it suck all the CPU power... but I guess it makes sense since the program is calling time() over and over again as fast as it can... I guess the reason should have been obvious.

My problem is I always seem to look for the hard way to do things!  :D

-- Roger

---

