---
title: "Please check how long does it take on your machine"
date: 2006-01-21
forum: Programming Talk
---

### Post by vetham on 2006-01-21
Hi
I'm making project connected to my studies and now I have to check very simple program on different processors. I'd apreciate if you could help me to test what time does it take to count 1234567^1234567 (on Ubuntu of course)
Program is here [http://www.mosus.xt.pl/pts/potegowanie.py](http://www.mosus.xt.pl/pts/potegowanie.py)
Thank you in advance

feel free to corect my English

---

### Post by 23meg on 2006-01-21
2 min 26 sec on my P4M Sonoma 740 running at 1.33 Ghz. I can test at other clock speeds if you like.

---

### Post by Stereotypical Rage on 2006-01-21
python potegowanie.py
time is 0 hours 1 min 8 sec

Athlon 64 3200+ (754)

---

### Post by Viro on 2006-01-21
I've got a slow machine ;)
```

time is 0 hours 4 min 18 sec

```

That's on a 1GHz Pentium 3.

---

### Post by kperkins on 2006-01-21
time is 0 hours 1 min 15 sec

Celeron D Processor 335 (2.8GHz), (laptop), 512mb RAM

---

### Post by thumper on 2006-01-21
time is 0 hours 2 min 32 sec
Intel 2.80GHz Hyper threading
2.6.12-10-686-smp

Kaffeine was playing a divx file at the time, but paused it and ran again, came up with the same results.

Perhaps a better timing would be cpu usage rather than elapsed time?

---

### Post by Viro on 2006-01-21
I was bored, and I was curious how fast the equivalent C code would run. So I wrote a similar benchmark, in C which uses the GMP library ;).

```

#include <gmp.h>
#include <time.h>
#include <stdio.h>

int main(void)
{
	mpz_t res;
	mpz_init(res);
	clock_t start, end;
	
	start = clock();
	mpz_ui_pow_ui(res, 12345678, 1234567);
	end = clock();
	printf("Time taken is %2.5lf seconds\n", (double)(end - start)/CLOCKS_PER_SEC);
	
	return 0;
}

```
If you're interested in compiling it, you need to pass the flag -lgmp (and be sure to install the package libgmp3-dev). On my machine, the result was 6.47 seconds. Not bad, considering it took 4 minutes and 18 seconds on the Python code. :)

---

### Post by briancurtin on 2006-01-21
time is 0 hours 1 min 38 sec

P4-HT 3.2 GHz 
2.6.12-10-686-smp

---

### Post by Viro on 2006-01-21
[QUOTE=thumper]time is 0 hours 2 min 32 sec
Intel 2.80GHz Hyper threading
2.6.12-10-686-smp

Kaffeine was playing a divx file at the time, but paused it and ran again, came up with the same results.

Perhaps a better timing would be cpu usage rather than elapsed time?[/QUOTE]

I'm guessing it's hyper threading that is giving you poor results. After all, this is a single threaded test that really pushes the CPU and the memory subsystem, having a 'fake' 2nd core isn't going to he helping things much.

---

### Post by LordHunter317 on 2006-01-21
[QUOTE=Viro]I'm guessing it's hyper threading that is giving you poor results. [/quote]No, it isn't, unless he's task switching for some bizzare reason.  Which he shouldn't be.

The only potential issue is a lack of memory bandwidth from doing other tasks.

---

### Post by newtonfn on 2006-01-21
Another pretty old machine.
3 min 18 sec on a Athlon 1Ghz (384mb ram)

---

### Post by Iandefor on 2006-01-21
```

ian@leviathan:~/Desktop$ python potegowanie.py
time is 0 hours 2 min 27 sec

``` 
AMD Sempron 2600+ rated at 1.6 ghz.

Viro: 
using your code, I got:
```

ian@leviathan:~$ ./bignum
Time taken is 2.36000 seconds

```
Mightily more efficient than Python, I must say!

---

### Post by cwaldbieser on 2006-01-21
[QUOTE=vetham]Hi
I'm making project connected to my studies and now I have to check very simple program on different processors. I'd apreciate if you could help me to test what time does it take to count 1234567^1234567 (on Ubuntu of course)
Program is here [http://www.mosus.xt.pl/pts/potegowanie.py](http://www.mosus.xt.pl/pts/potegowanie.py)
Thank you in advance

feel free to corect my English[/QUOTE]
time is 0 hours 1 min 31 sec
```

$cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping	: 9
cpu MHz		: 2993.548
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips	: 5931.00

```

---

### Post by Wallakoala on 2006-01-21
time is 0 hours 1 min 12 sec

intel pentium 4 3.4 w/ ht

...do I win?

---

### Post by Jessehk on 2006-01-21
I'll copy cwaldbieser's approach:

> 
time is 0 hours 2 min 10 sec


> 

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 9
cpu MHz         : 2993.477
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5931.00



---

### Post by lcg on 2006-01-21
[QUOTE=vetham]I'd apreciate if you could help me to test what time does it take to count 1234567^1234567 (on Ubuntu of course)
Program is here [http://www.mosus.xt.pl/pts/potegowanie.py](http://www.mosus.xt.pl/pts/potegowanie.py)
Thank you in advance[/QUOTE]
The Python code you posted calculates 1234567**8**^1234567, not 1234567^1234567. A mistake?

Anyway:
```
time ./test.py
time is 0 hours 3 min 0 sec

real    3m0.309s
user    2m36.632s
sys     0m0.650s
```

That's on a Pentium M (Banias) with 1.5 GHz.

[QUOTE=Wallakoala]...do I win?[/QUOTE]
No. ;)
```
time ./test.py
time is 0 hours 1 min 7 sec

real    1m6.893s
user    1m5.880s
sys     0m0.352s
```

That result is from an Athlon 64 3000+ (1.8 GHz). I could also offer results from an Athlon 64 3500+, but I'd have to get up for that because the box is powered down right now. ;)

Lars

---

### Post by majikstreet on 2006-01-21
time is 0 hours 2 min 4 sec

CPU Intel(R) Celeron(R) CPU 2.20GHz, 2193Mhz, 128KB Cache, 4389 BMIPs

```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Celeron(R) CPU 2.20GHz
stepping        : 7
cpu MHz         : 2193.167
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid
bogomips        : 4389.27

```

---

### Post by transactionlogfiller on 2006-01-21
```
./bignum 
time is 0 hours 3 min 5 sec

cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm) XP 1900+
stepping        : 0
cpu MHz         : 1461.348
cache size      : 512 KB
```

Edit: - That was vetham's python code, not the C code.

---

### Post by Greg2 on 2006-01-21
Mobile AMD Sempron(tm) Processor 2800+

time is 0 hours 2 min 17 sec

---

### Post by bloodborne on 2006-01-23
2 min 11 sec, specs are in my sig.

---

### Post by dimis on 2006-01-23
ok. Here are my results on an AMD-64@3000+ (s754) - motherboard: MSI K8N Neo Platinum with 1GB RAM - no overclocking:
```
dimis@crag-hack:~/Desktop$ cat potegowanie.py
#!/usr/bin/python
import time
a=time.gmtime()
12345678**1234567
b=time.gmtime()
print "time is",abs(a[3]-b[3]),'hours',abs(a[4]-b[4]),'min',abs(a[5]-b[5]),'sec'
dimis@crag-hack:~/Desktop$ python potegowanie.py
time is 0 hours 1 min 13 sec
dimis@crag-hack:~/Desktop$
```
Hope these times can help you with your project. However I encourage you (and everybody else ofcourse) to have a look on a thread I just started [here](http://www.ubuntuforums.org/showthread.php?p=676481#post676481) with similar content but regarding AMD-64bit processors' performance.

Regards,
Dimis

---

### Post by Revert on 2006-01-23
time is 0 hours 2 min 33 sec

Athlon XP 3000+ (2.16ghz, if I recall correctly).

---

### Post by Gus-O-Matic on 2006-01-24
[QUOTE=Viro]I was bored, and I was curious how fast the equivalent C code would run. So I wrote a similar benchmark, in C which uses the GMP library ;).
[/QUOTE]

Your benchmark isn't really similar at all .... here is the python equivalent of what you wrote, and it runs in 4 seconds on my machine (1.4ghz Pentium M, 512mb RAM, 2 mins 16 for the original code)

```

import time
import gmpy
a=time.gmtime()
pow(gmpy.mpz(12345678),gmpy.mpz(1234567))
b=time.gmtime()
print "time is",abs(a[3]-b[3]),'hours',abs(a[4]-b[4]),'min',abs(a[5]-b[5]),'sec'

```

---

### Post by Viro on 2006-01-24
[QUOTE=Gus-O-Matic]Your benchmark isn't really similar at all .... here is the python equivalent of what you wrote, and it runs in 4 seconds on my machine (1.4ghz Pentium M, 512mb RAM, 2 mins 16 for the original code)

```

import time
import gmpy
a=time.gmtime()
pow(gmpy.mpz(12345678),gmpy.mpz(1234567))
b=time.gmtime()
print "time is",abs(a[3]-b[3]),'hours',abs(a[4]-b[4]),'min',abs(a[5]-b[5]),'sec'

```[/QUOTE]

Why is it not similar? C has no built-in support for big integers, and as such you have to depend on a C library like GMP or you can write your own. Since I'm lazy, I use what others have written. 

Python of course, has pathetic performance, and the only way it can approach C-like performance, is as you have demonstrated. To call a C library :). There is far more C in your code than there is Python, so really, it is just C code :).

---

### Post by Gus-O-Matic on 2006-01-24
my point is that python can be fast enough when used correctly ... and its easy to do exactly that.  Your point about it using a C library is irrelevant, python is mostly written in C anyway ...

---

### Post by Viro on 2006-01-24
Of course, when used 'correctly'. Python can perform well, provided there is a C library that performs a particular task for it. What happens when there isn't one? Of course, you could code all the necessary routines in C and then call them from Python, but then why use Python for Python's sake? You'd be better off just writing it in C.

---

### Post by gord on 2006-01-24
python should do the clever stuff and c should do the grunt work, thats how i do it.

also, allthough i doubt it would make any diffirence here seing as the number is a bit large, [psyco](http://psyco.sourceforge.net/) is your friend ;)

---

### Post by public_void on 2006-01-24
Intel Pentium M processor 1.60GHz
I don't what happened but first time it came up with "time is 1 hours 58 min 28 sec". Second time round "time is 0 hours 2 min 1 sec".

---

### Post by ubuntumaneh on 2006-01-24
In an old computer with 400Mhz, 160kB of mem (AMD-K6):

time is 0 hours 20 min 26 sec

---

### Post by bfutrell on 2006-01-24
6 minutes, 52 seconds Athlon 700mhz (Slot A), 384MB RAM Was looking at this web site at the time with Konqueror, so I'll try again.

2nd try with no other windows open:  5 minutes, 32 seconds.

---

### Post by jerome bettis on 2006-01-24
[quote=bloodborne]2 min 11 sec, specs are in my sig.[/quote] 
lol i have the same machine,

time is 0 hours 2 min 5 sec

6 seconds faster bitches!!! :p

pentium M 1.7 ghz, i have the 2mb L2 cache, do you have that?

---

### Post by SamH on 2006-01-24
time is 0 hours 1 min 50 sec

AMD Sempron 2600 +, 512 MB DDR400 RAM

---

### Post by jerome bettis on 2006-01-24
ok i just rebooted and turned high performance mode on in the bios,

time is 0 hours 1 min 35 sec

what a difference a little more voltage makes lol, i'd keep it like this all the time if it didn't get so damn hot!

that just goes to show you that 1.7 ghz, 2.4 ghz etc etc is nothing more than a number!! there's so many other factors that affect performance, and different programs will perform better on certain machines than other ones that may appear to be better.

---

### Post by nrwilk on 2006-01-25
Based on other people's results, this seems very wrong.

time is 0 hours 2 min 53 sec

> processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 47
model name      : AMD Athlon(tm) 64 Processor 3500+
stepping        : 0
cpu MHz         : 2210.356
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips        : 4425.18


Is there anything I can do about my performance?  I haven't noticed any lagginess or the like, but maybe I'm not running as fast as I could be...

---

### Post by jerome bettis on 2006-01-25
[quote=Fealos]Based on other people's results, this seems very wrong.

time is 0 hours 2 min 53 sec



Is there anything I can do about my performance?  I haven't noticed any lagginess or the like, but maybe I'm not running as fast as I could be...[/quote]

i don't think this has been mentioned, anytime you are going to do some sort of benchmark, it has to be done in the most ideal conditions as possible, i.e. single user mode with a fresh login.  otherwise other processes can get swapped in and that completely throws the results off.

sudo init 1 to go single user mode
sudo init 2 to get back

---

### Post by nrwilk on 2006-01-25
[QUOTE=jerome bettis]sudo init 1 to go single user mode
sudo init 2 to get back[/QUOTE]

Much better!  Thanks, man.


time is 0 hours 1 min 1 sec


> 
processor : 0
vendor_id : AuthenticAMD
cpu family : 15
model : 47
model name : AMD Athlon(tm) 64 Processor 3500+
stepping : 0
cpu MHz : 2210.356
cache size : 512 KB
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 1
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips : 4425.18


---

### Post by spartas on 2006-01-30
Using the standard runlevel with a single Xeon 3.0Ghz proc took 
```

tim@asynjur:~$ python potegowanie.py 
time is 0 hours 1 min 10 sec

```

Note: this is with a server install (No X) using the following kernel
```

tim@asynjur:~$ uname -a
Linux asynjur 2.6.12-10-amd64-generic #1 Thu Dec 22 10:56:42 UTC 2005 x86_64 GNU/Linux

```

---

### Post by slavik on 2006-01-30
try a perl version :P (I doubt you could use gmp though, unless the package is available)

---

### Post by Single on 2006-01-31
1 min 42 sec.

```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.86GHz
stepping        : 8
cpu MHz         : 797.914
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx est tm2
bogomips        : 1576.09

```

---

### Post by anthro398 on 2006-01-31
time is 0 hours 1 min 1 sec

Xeon 2.8 Ghz, single processor

---

### Post by rock freak on 2006-01-31
0m 59s

AMD (San Diego) Athlon 64bit 4000+ 939pin
2Gb RAM (neva used it all yet :P)

---

### Post by bicchi on 2006-01-31
1 min 7 sec

Linux localhost 2.6.12-10-amd64-k8 #1 Mon Jan 16 17:23:13 UTC 2006 x86_64 GNU/Linux
AMD Athlon 64 3500+ Socket 939 (Newcastle core), MSI K8N Neo2 Platinum, 1 GB DDR400 RAM

---

### Post by Eleaf on 2006-02-04
Time is _0 hours 1 min 10 sec_

= )  I'm running an AMD Sempron 2800+ .  512 megs ddr ram...
I overclocked this about 300 mhz.  Running in gnome, not a lower level runlevel.

```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 44
model name      : AMD Hammer Family processor - Model Unknown
stepping        : 2
cpu MHz         : 1959.806
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni
bogomips        : 3883.00

```

---

### Post by Viro on 2006-02-04
> time is 0 hours 2 min 7 sec

Feeling a little bored, I ran the file on my Powerbook G4 1.33 GHz running Mac OS X Tiger. Not a bad result, nearly twice the speed of my old Pentium III 1GHz, and about the same speed as a 1.33 GHz Pentium M. 

This only goes to show how artificial this benchmark really is, a G4 performing as well as a Pentium M :).

---

### Post by Eleaf on 2006-02-04
[QUOTE=Viro]Feeling a little bored, I ran the file on my Powerbook G4 1.33 GHz running Mac OS X Tiger. Not a bad result, nearly twice the speed of my old Pentium III 1GHz, and about the same speed as a 1.33 GHz Pentium M. 

This only goes to show how artificial this benchmark really is, a G4 performing as well as a Pentium M :).[/QUOTE]

Why would a g4 NOT perform as well as a Pentium M?  I thought powerpc was supposed to be quite a bit faster than intel... ;)

---

### Post by Iandefor on 2006-02-04
[quote=Eleaf]Why would a g4 NOT perform as well as a Pentium M? I thought powerpc was supposed to be quite a bit faster than intel... ;)[/quote] Please tell me you're joking ;).

---

### Post by Viro on 2006-02-05
I am comparing processors. You're comparing instruction sets against a company. I need not say more.

---

### Post by spartas on 2006-02-06
Here's one for you all: I mentioned earlier the python code took 1m 10s on my single 3.0Ghz Xeon, however, anthros posted after me that it took 1m 1s on a 2.8 Xeon proc.  My system has low usage most of the time; this is an interesting observation.

I do not know which kernel anthros is using, but I am still using a generic x86_64 kernel.

---

### Post by anthro398 on 2006-02-27
[QUOTE=spartas]Here's one for you all: I mentioned earlier the python code took 1m 10s on my single 3.0Ghz Xeon, however, anthros posted after me that it took 1m 1s on a 2.8 Xeon proc.  My system has low usage most of the time; this is an interesting observation.

I do not know which kernel anthros is using, but I am still using a generic x86_64 kernel.[/QUOTE]

anthro398@dli:~$ uname -r
2.6.12-10-686

I'm using a 32 bit kernel.

---

### Post by Alpha_toxic on 2006-02-27
time is 0 hours 5 min 47 se

this is on PIII @ 733MHz x2 , but I guess that it was only using one of the processors. For sure it can't be that slow if using both...

---

### Post by Klaidas on 2006-02-27
Intel Pentium 4 1,7 GHz
512 mb of RAM

Results:
> time is 0 hours 3 min 1 sec


---

### Post by Klaidas on 2006-02-27
I have just tried it under recovery mode (no x or anythingt :) )

The result was 2 min 17 sec

---

### Post by jannol on 2006-02-27
P4 Prescott 3000@3900
time is 0 hours 1 min 0 sec

in recovery mode
time is 0 hours 0 min 49 sec

---

### Post by krypto_wizard on 2006-02-27
1 min 18 sec on AMD Athlon 3100 (desktop)

2 min 24 sec on Intel Pentium M 1.67 GHz (laptop)

---

### Post by Scotland on 2006-02-27
time is 0 hours 1 min 19 sec

Intel Core Duo 2.16 Mhz on a Dell Inspiron 9400 (laptop)

Dougie.

---

### Post by Klaidas on 2006-02-27
It would be interesting to test it under Windoze ;)))

---

### Post by jannol on 2006-02-27
[QUOTE=Klaidas]It would be interesting to test it under Windoze ;)))[/QUOTE]

How do you mean? simply running this script?

It would probably give very similar result I guess.

I tried superpi in windows and ubuntu and it is a bit faster in ubuntu but afaik, there is stuff that differ so it is not comparable so superpi linux results can not compete with superpi windows results.

---

### Post by awi on 2006-02-27
```
$ python potegowanie.py
time is 0 hours 2 min 26 sec
```

Sempron 64 - 2500+ (1.4GHz). RAM: 1GB @ 400MHz

---

### Post by muaddib on 2006-02-28
1 min 11 sec
On my AMD Athlon 64 3500+

---

### Post by flapane on 2006-02-28
how can i open it? i tried python filename but it loaded only its code...

about superpi it's 5secs faster here, it's not coomparable with windoze

---

### Post by gezzabob on 2006-05-01
~$ uname -a
Linux ubuntu 2.6.12-10-k7 #1 Sat Mar 11 16:59:38 UTC 2006 i686 GNU/Linux

~$cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm) XP 2600+
stepping        : 0
cpu MHz         : 1913.498
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips        : 3792.89

~$ python potegowanie.py
time is 0 hours 2 min 20 sec

---

### Post by lovebyte on 2006-05-02
On my dual core:

time is 0 hours 1 min 26 sec

#509% cat /proc/cpuinfo (only some info shown)
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2500  @ 2.00GHz
....
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 4006.41

... etc (for the second core!)

---

### Post by biocrasher on 2006-05-02
Here's an interesting result:

~$ cat /proc/cpuinfo
> processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 4
cpu MHz         : 3216.803
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl cid xtpr
bogomips        : 6373.37

python2.3 potegowanie.py
time is 0 hours 3 min 7 sec


python2.4 potegowanie.py
time is 0 hours 1 min 9 sec

---

### Post by Kimm on 2006-05-02
Intel Celeron (something) 1.7 Ghz

> 
kim@ubuntu:~$ python potegowanie.py
time is 0 hours 3 min 0 sec


I need a new computer...

---

### Post by auroraborealis on 2006-05-02
2x P4 3.4ghz, 1gb RAM

1 min, 4 secs

---

### Post by simplyw00x on 2006-05-03
carl@ubuntu:~$ python potegowanie.py 
time is 0 hours 3 min 17 sec
carl@ubuntu:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 6
model		: 8
model name	: AMD Athlon(tm) XP 2000+
stepping	: 0
cpu MHz		: 1667.002
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips	: 3335.68
carl@ubuntu:~$ uname -a
Linux ubuntu 2.6.15-21-686 #1 SMP PREEMPT Fri Apr 21 16:57:03 UTC 2006 i686 GNU/Linux

---

### Post by Atomic Dog on 2006-09-11
ubuntu:~/Desktop$ python potegowanie.py
time is 0 hours 2 min 3 sec
ubuntu:~/Desktop$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Celeron(R) M processor         1.50GHz
stepping        : 8
cpu MHz         : 1496.470
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe
bogomips        : 2997.46

---

