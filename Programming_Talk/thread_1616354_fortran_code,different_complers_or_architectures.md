---
title: "fortran code,different complers or architectures"
date: 2010-11-08
forum: Programming Talk
---

### Post by Nikolazigic on 2010-11-08
I have a problem with one FORTRAN 77 code,the guy who has written it worked on SUN Unix.I am using x86-64 bit machine,now fort77(tried with Intel 11.1 compiler but it was hell.Code:
c        patched for g77 compilation
      character*72 ifname,ofname
c
      write(*, fmt="(/'Enter input file name')")
      read(5,85) ifname
85    format(a72)
      write(*, fmt="(/'Enter output file name')")
      read(5,85) ofname
c
      open(unit=11, file=ifname, form='unformatted', status='old')
      open(unit=12, file=ofname)
      n=0
c
100   read(11, end=999) x,y,z,t,u,i
      write(12,5) x,y,z,t,u,i
5     format(5f10.3,i3)
      n=n+1
      go to 100
c
999   write(6,1) n
1     format(/'number of lines in file: ',i10/)
c
      stop
      end
I got this:
      .000      .500      .000      .025       nan 24
      .000      .010      .442      .025      .000 24
      .000      .010      .230      .025      .000 24
      .000      .010      .171      .025      .000 24
      .000      .010      .332      .025      .000 24
      .000      .010      .483      .025      .000 24
      .000      .010      .684      .025      .000 24
WHY DO I HAVE NAN?

---

### Post by Arndt on 2010-11-08
> **Nikolazigic said:**
> I have a problem with one FORTRAN 77 code,the guy who has written it worked on SUN Unix.I am using x86-64 bit machine,now fort77(tried with Intel 11.1 compiler but it was hell.Code:
c        patched for g77 compilation
      character*72 ifname,ofname
c
      write(*, fmt="(/'Enter input file name')")
      read(5,85) ifname
85    format(a72)
      write(*, fmt="(/'Enter output file name')")
      read(5,85) ofname
c
      open(unit=11, file=ifname, form='unformatted', status='old')
      open(unit=12, file=ofname)
      n=0
c
100   read(11, end=999) x,y,z,t,u,i
      write(12,5) x,y,z,t,u,i
5     format(5f10.3,i3)
      n=n+1
      go to 100
c
999   write(6,1) n
1     format(/'number of lines in file: ',i10/)
c
      stop
      end
I got this:
      .000      .500      .000      .025       nan 24
      .000      .010      .442      .025      .000 24
      .000      .010      .230      .025      .000 24
      .000      .010      .171      .025      .000 24
      .000      .010      .332      .025      .000 24
      .000      .010      .483      .025      .000 24
      .000      .010      .684      .025      .000 24
WHY DO I HAVE NAN?

What does the input file look like?

---

### Post by Nikolazigic on 2010-11-08
Input file is:
0000000 0018 0000 0000 4040 0000 0000 0000 3f00
0000020 0000 0000 cccd 3ccc ffff ffff 0018 0000
0000040 0018 0000 0000 3f80 0000 0000 d70a 3c23
0000060 4dd3 3ee2 cccd 3ccc 0001 0000 0018 0000
0000100 0018 0000 0000 4000 0000 0000 d70a 3c23
0000120 851f 3e6b cccd 3ccc 0001 0000 0018 0000
0000140 0018 0000 0000 4060 0000 0000 d70a 3c23
0000160 1aa0 3e2f cccd 3ccc 0001 0000 0018 0000
0000200 0018 0000 0000 4090 0000 0000 d70a 3c23
0000220 fbe7 3ea9 cccd 3ccc 0001 0000 0018 0000
0000240 0018 0000 0000 40b0 0000 0000 d70a 3c23
0000260 4bc7 3ef7 cccd 3ccc 0001 0000 0018 0000
0000300 0018 0000 0000 40d0 0000 0000 d70a 3c23
0000320 1aa0 3f2f cccd 3ccc 0001 0000 0018 0000
0000340 0018 0000 0000 40f0 0000 0000 d70a 3c23
0000360 70a4 3f5d cccd 3ccc 0001 0000 0018 0000
0000400 0018 0000 0000 4108 0000 0000 d70a 3c23
0000420 f3b6 3f8d cccd 3ccc 0001 0000 0018 0000
This is hex output.

---

### Post by Nikolazigic on 2010-11-08
The program has been compiled with f77,is this may be issue?

---

### Post by Nikolazigic on 2010-11-09
od -d output:
0000000    24     0     0 16448     0     0     0 16128
0000020     0     0 52429 15564 65535 65535    24     0
0000040    24     0     0 16256     0     0 55050 15395
0000060 19923 16098 52429 15564     1     0    24     0
0000100    24     0     0 16384     0     0 55050 15395
0000120 34079 15979 52429 15564     1     0    24     0
0000140    24     0     0 16480     0     0 55050 15395
0000160  6816 15919 52429 15564     1     0    24     0
0000200    24     0     0 16528     0     0 55050 15395
0000220 64487 16041 52429 15564     1     0    24     0
0000240    24     0     0 16560     0     0 55050 15395
0000260 19399 16119 52429 15564     1     0    24     0
0000300    24     0     0 16592     0     0 55050 15395
0000320  6816 16175 52429 15564     1     0    24     0
0000340    24     0     0 16624     0     0 55050 15395
0000360 28836 16221 52429 15564     1     0    24     0

---

