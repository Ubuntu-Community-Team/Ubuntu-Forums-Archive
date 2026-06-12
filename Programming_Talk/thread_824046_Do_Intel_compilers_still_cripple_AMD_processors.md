---
title: "Do Intel compilers still cripple AMD processors?"
date: 2008-06-09
forum: Programming Talk
---

### Post by Silpheed2K on 2008-06-09
Just curious cause I'd rather use GCC if this is still going on. [which is open source and dang near just as fast from what i read]
I dont need my code crashing because it's an AMD processor and underhanded business practices.
So does anybody know if the Intel 10.1 compilers still do this?
[http://yro.slashdot.org/article.pl?sid=05/07/12/1320202&tid=142&tid=118&tid=123](http://yro.slashdot.org/article.pl?sid=05/07/12/1320202&tid=142&tid=118&tid=123)

---

### Post by Phenax on 2008-06-09
AMD processors can run ICC-compiled binaries. ICC will optimize better for Intel processors (many think that they have specifically disabled faster routes on non-Intel processors). AMD processors will likely still get a better performance boost from using ICC over GCC either way.

---

### Post by Silpheed2K on 2008-06-09
Now that I've looked further into it.. it seems that it MAY still do that..
I ran across this page and somebody was examining the compiler closely and they found binary it in that does do that.
[http://www.swallowtail.org/naughty-intel.html](http://www.swallowtail.org/naughty-intel.html)
so it's probably still in 10.0 although it was in 9.0.. if anybody has anymore info let me know.

---

### Post by Phenax on 2008-06-09
Well, it works for me, and is faster on my AMD processor (Not tested significantly). The only problem I had was that it was unable to run code compiled for SSE3 on my processor (-xP) when my processor has SSE3 technologies (*). Enabling SSE2 was not problematic, though.

*> 
Fatal Error: This program was not built to run on the processor in your system.
The allowed processors are: Intel(R) Pentium(R) 4 and compatible Intel processors with Streaming SIMD Extensions 3 (SSE3) instruction support.

> 
$ cat /proc/cpuinfo | grep pni
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps


An example of this is a naive Ackermann function in GCC vs ICC.

[php]
unsigned int naive_ackermann(unsigned int m, unsigned int n) {
    if(m == 0)
        return n + 1;
    else if (n == 0)
        return naive_ackermann(m - 1, 1);
    else
        return naive_ackermann(m - 1, naive_ackermann(m, n - 1));
}
[/php]naive_ackermann(3, 12) on an AMD64.
> 
$gcc ack.c
$time ./a.out 
real    0m5.630s
user    0m5.604s
sys    0m0.016s

$ icc ack.c
$ time ./a.out 
real    0m1.912s
user    0m1.908s
sys    0m0.000s

$ gcc -O3 -march=k8 ack.c
$ time ./a.out 
real    0m2.018s
user    0m2.012s
sys    0m0.008s

$ icc -O3 -ipo ack.c
ipo: remark #11001: performing single-file optimizations
ipo: remark #11005: generating object file /tmp/ipo_iccc2I5K5.o
$ time ./a.out 
real    0m1.792s
user    0m1.792s
sys    0m0.000s

$ icc -O3 -ipo -xW ack.c
ipo: remark #11001: performing single-file optimizations
ipo: remark #11005: generating object file /tmp/ipo_icc8gRGBQ.o
$ time ./a.out 
real    0m1.698s
user    0m1.700s
sys    0m0.004s


---

### Post by Phenax on 2008-06-09
> **Silpheed2K said:**
> Now that I've looked further into it.. it seems that it MAY still do that..
I ran across this page and somebody was examining the compiler closely and they found binary it in that does do that.
[http://www.swallowtail.org/naughty-intel.html](http://www.swallowtail.org/naughty-intel.html)
so it's probably still in 10.0 although it was in 9.0.. if anybody has anymore info let me know.

I would hardly call this crippling;
I've applied the patch on that website. It seemingly enables me to compile an SSE3 binary properly. Here are the results:
> 
$ icc -O3 -ipo -xP ack.c
ipo: remark #11001: performing single-file optimizations
ipo: remark #11005: generating object file /tmp/ipo_iccZqNC7g.o
$ time ./a.out 
real    0m1.621s
user    0m1.612s
sys    0m0.000s


---

### Post by Silpheed2K on 2008-06-09
> **Phenax said:**
> I would hardly call this crippling;
I've applied the patch on that website. It seemingly enables me to compile an SSE3 binary properly. Here are the results:

That's the point of the patch... so it doesn't restrict certain functions and optimizations to Intel processors only.
What version of the intel compiler did you patch? I wonder if it will work for me and I have 10.1

---

### Post by Phenax on 2008-06-10
> **Silpheed2K said:**
> That's the point of the patch... so it doesn't restrict certain functions and optimizations to Intel processors only.
What version of the intel compiler did you patch? I wonder if it will work for me and I have 10.1

It will work for 10.1. Stick it in icc/lib directory and run it.

---

### Post by Silpheed2K on 2008-06-10
I'm trying to run it but some some reason it keeps saying libirc.a not found when i enter
```
sudo perl '/opt/intel/cc/10.1.015/lib/intel_check_patch'
```
I see the file sitting right there

---

### Post by Phenax on 2008-06-10
> **Silpheed2K said:**
> I'm trying to run it but some some reason it keeps saying libirc.a not found when i enter
```
sudo perl '/opt/intel/cc/10.1.015/lib/intel_check_patch'
```I see the file sitting right there

Try to cd to /opt/intel/cc/10.1.015/lib and then do perl intel_check_patch

---

### Post by Silpheed2K on 2008-06-10
Thanks that did the trick.. I'm glad at least we both got something out of this.. thanks for the help.

Here's the output (also for anybody who runs across this on a search)
```
rex@rex-desktop:~$ cd /opt/intel/cc/10.1.015/lib
rex@rex-desktop:/opt/intel/cc/10.1.015/lib$ sudo perl intel_check_patch
[sudo] password for rex:
Patching compiler libraries...
Patching libiomp5.a in 6 places...Patch operation successful, original file at 'libiomp5.a.orig'
Patching libguide_stats.so in 6 places...Patch operation successful, original file at 'libguide_stats.so.orig'
Patching libguide.so in 6 places...Patch operation successful, original file at 'libguide.so.orig'
Patching libirc_fp.a in 3 places...Patch operation successful, original file at 'libirc_fp.a.orig'
Patching libomp_db.so in 3 places...Patch operation successful, original file at 'libomp_db.so.orig'
Patching libiompprof5.so in 6 places...Patch operation successful, original file at 'libiompprof5.so.orig'
Patching libguide.a in 6 places...Patch operation successful, original file at 'libguide.a.orig'
Patching libirc.so in 3 places...Patch operation successful, original file at 'libirc.so.orig'
Patching libirc_pic.a in 3 places...Patch operation successful, original file at 'libirc_pic.a.orig'
Patching libimf.so in 3 places...Patch operation successful, original file at 'libimf.so.orig'
Patching libiompprof5.a in 6 places...Patch operation successful, original file at 'libiompprof5.a.orig'
Patching libiomp5.so in 6 places...Patch operation successful, original file at 'libiomp5.so.orig'
Patching libsvml.so in 3 places...Patch operation successful, original file at 'libsvml.so.orig'
Patching libirc.a in 3 places...Patch operation successful, original file at 'libirc.a.orig'
Patching libguide_stats.a in 6 places...Patch operation successful, original file at 'libguide_stats.a.orig'

```

---

