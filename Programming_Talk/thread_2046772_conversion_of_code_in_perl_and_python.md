---
title: "conversion of code in perl and python"
date: 2012-08-23
forum: Programming Talk
---

### Post by learnbash on 2012-08-23
How to convert below bash code in perl and python.


```

  for BLOCK in /sys/block/emcpow* 

do         
echo "100000" > "$BLOCK"/queue/nr_requests         
echo "noop" > "$BLOCK"/queue/scheduler 

done 
```

---

### Post by trent.josephsen on 2012-08-23
Perl (untested):
```
for (glob '/sys/block/emcpow*') {
    open REQ, '>', "$_/queue/nr_requests";
    print REQ "100000\n";
    close REQ;

    open SCHED, '>', "$/queue/scheduler";
    print SCHED "noop\n";
    close SCHED;
}
```
Don't know why you'd want to do that though; the bash version makes a lot more sense.

---

### Post by learnbash on 2012-08-23
Below script not changing the values, it is not working correctly.

> **trent.josephsen said:**
> Perl (untested):
```
for (glob '/sys/block/emcpow*') {
    open REQ, '>', "$_/queue/nr_requests";
    print REQ "100000\n";
    close REQ;

    open SCHED, '>', "$/queue/scheduler";
    print SCHED 'noop';
    close SCHED;
}
```

---

### Post by trent.josephsen on 2012-08-23
I forgot to add a newline to "noop" (edited in my prior post).

If that doesn't fix your problem, well, I don't know why. Do you understand how it works or did you just copy and paste it?

Run it with perl -w at least to enable warnings.

---

