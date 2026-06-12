---
title: "Timing for DebugFS?"
date: 2012-01-20
forum: Programming Talk
---

### Post by mcginnda on 2012-01-20
Hi All,

I want to be able to correlate the data I'm getting from tracing through the DebugFS (particularly syscalls and sched_switch events) with data I am gathering elsewhere. I'm running Ubuntu 10.10 on an Intel i5 machine.

The problem is that the time information in DebugFS doesn't seem to be from any available function, and doesn't seem to even be using the same frequency. 

For example, for a run of 5.5 seconds according to gettimeofday and clock_gettime, the difference in the first and last entries in the trace is 5 seconds. This difference isn't acceptable for my uses, and is well beyond what I would expect the time to turn on tracing would be. Correlating using system calls helps some, but it is still in the 0.25 - 0.5 second range. This seems to be contstant across wait times.

My test code for this is below:
```
   #define TRACE_FORMAT "%*[^-]-%*d [%*d] %d.%d:"
    uint64_t       firstTime    = 0;
    uint64_t       lastTime     = 0;
    uint64_t       firstTSC     = 0;
    uint64_t       lastTSC      = 0;
    char           line[200]    = "";
    uint64_t       seconds      = 0;
    uint64_t       ns           = 0;
    uint64_t       waitPeriod   = 10;
    struct timeval tv           = {0};
    
    //Start targeting
    system("mount -t debugfs nodev /sys/kernel/debug 2> /dev/null");
    system("echo sched_switch > /sys/kernel/debug/tracing/current_tracer");
    system("echo verbose > /sys/kernel/debug/tracing/trace_options");
    system("echo 1 > /sys/kernel/debug/tracing/events/syscalls/enable");
    system("echo > /sys/kernel/debug/tracing/trace");
    gettimeofday(&tv, NULL);
    fprintf(fp, "1");
    fseek(fp, 0, SEEK_SET);
    firstTime = ((uint64_t) tv.tv_sec) * 1000000000 +
        ((uint64_t) tv.tv_usec * 1000);
    for(i = 0; i < waitPeriod; i++)
    {
        usleep(500000);
        fprintf(stderr, ".");
    }
    fprintf(stderr, "\n");
    system("cat /sys/kernel/debug/tracing/trace > /tmp/trace.txt");
    fprintf(fp, "0");
    gettimeofday(&tv, NULL);
    lastTime = ((uint64_t) tv.tv_sec) * 1000000000 +
        ((uint64_t) tv.tv_usec * 1000);

    fclose(fp);
    fp = fopen("/tmp/trace.txt", "r");
    firstTSC = 0;
    while(fgets(line, 200, fp) != NULL)
    {
        if(sscanf(line, TRACE_FORMAT, &seconds, &ns) != 2)
        continue;
        lastTSC = seconds * 1000000000 + ns * 1000;
        if(firstTSC == 0)
        firstTSC = lastTSC;
    }
    fprintf(stderr, "%25s %12llu ns\n", "Trace Duration: ",
        lastTSC - firstTSC);
    fprintf(stderr, "%25s %12llu ns\n", "Actual Duration: ",
        lastTime - firstTime);
    fprintf(stderr, "%25s %12Lf\n", "Trace to Second Scale: ",
        ((long double) (lastTSC - firstTSC)) /
        ((long double) (lastTime - firstTime)));
    if(lastTime - firstTime < lastTSC - firstTSC)        
        fprintf(stderr, "%25s %12llu ns\n", "Trace Error: -",
            (lastTSC - firstTSC) - (lastTime - firstTime));
    else    
        fprintf(stderr, "%25s %12llu ns\n", "Trace Error: ",
            (lastTime - firstTime) - (lastTSC - firstTSC));

```Is there a function I'm missing that gives this timestamp, or is there some variable I can access that will translate trace  time into gettimeofday time? 

Thanks for any help you can give!

---

