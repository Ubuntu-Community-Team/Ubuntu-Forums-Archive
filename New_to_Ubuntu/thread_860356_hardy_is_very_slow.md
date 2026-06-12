---
title: "hardy is very slow"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Marianne_S on 2008-07-15
I've had problems with 8.04 running very slow since i installed it. Right now i have xubuntu 64 bit but i had the same problem with the 32 bit version of xubuntu and ubuntu (yes i have been switching alot these past months, can't seem to make up my mind). it is better with 64 bit xubuntu, but still not very good.

i have a hp pavillion a6025 with 1 gb memory.

i ran atop in the terminal after booting - and i can't interpet the information. i do notice however that it is using alot of memory when it shouldn't.

any suggestion as to where to look, or things to do is appreciated.

here is what atop "said":
> 
ATOP - m-desktop          2008/07/15  20:01:42               10 seconds elapsed
PRC | sys   0.09s | user   0.56s | #proc    116 | #zombie    0 | #exit      ? |
CPU | sys      1% | user      6% | irq       0% | idle    192% | wait      0% |
cpu | sys      0% | user      2% | irq       0% | idle     97% | cpu000 w  0% |
cpu | sys      1% | user      4% | irq       0% | idle     95% | cpu001 w  0% |
CPL | avg1   0.01 | avg5    0.11 | avg15   0.16 | csw     7301 | intr    3307 |
MEM | tot    1.0G | free  292.2M | cache 345.8M | buff   14.5M | slab   30.4M |
SWP | tot    2.4G | free    2.4G |              | vmcom 459.3M | vmlim   2.9G |
DSK |         sda | busy      0% | read       4 | write     22 | avio    1 ms |
NET | network     | ipi        3 | ipo        0 | ipfrw      0 | deliv      0 |
NET | eth0   ---- | pcki     218 | pcko       0 | si   11 Kbps | so    0 Kbps |

  PID MINFLT MAJFLT      VSTEXT  VSIZE  RSIZE  VGROW  RGROW  MEM CMD     1/1   
 6593     11      0      13228K 382.9M 124.1M     0K     0K  12% opera
 5632      0      0       1761K 144.3M 42300K  -352K     0K   4% Xorg
 6540      0      0        154K 184.0M 24420K     0K     0K   2% xfce4-terminal
 6310      0      0        196K 201.0M 17152K     0K     0K   2% nm-applet
 6277      0      0        539K 134.8M  5748K     0K     0K   1% Thunar
 6563    429      0        105K 13540K  1768K     0K     0K   0% atop
 2590      0      0          0K     0K     0K     0K     0K   0% kjournald
 4505      0      0          0K     0K     0K     0K     0K   0% kjournald


---

### Post by bobnutfield on 2008-07-15
I don't see much in the results you have posted to indicated why you would be getting slow performance.  You have a third of your memory in cache (awaiting use) and a third free with two thirds in use.  There is little or no CPU usage.

A lot of things can contribute to slow performance, disk seek times, for example can cause very slow performance on some machines.

A better indication of what resources are being used is the top command which, when left running, will show what process is using what resources.

I know that doesn't help solve your problem, but if you can narrown down what processes are causing the slow performance,you may be able to fix it.

Bob

---

### Post by Marianne_S on 2008-07-15
hm see the litte i *thought* i could interpet i got wrong. 

I will try top and see if i learn something.

---

