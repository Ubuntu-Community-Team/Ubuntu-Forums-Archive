---
title: "Could Someone Compile This Fortran Code?"
date: 2010-01-17
forum: Programming Talk
---

### Post by MShaw on 2010-01-17
Could some please compile this and tell me the last value of n and i. I want to see if it works.

> program sieve_t
implicit none
integer*1 s(1000000), offset (10), sequence
integer i, j, n

n=0
sequence=4

do i=1, 10
offset(i)=0
enddo

offset(1)=2
offset(2)=4
offset(3)=2

do i=1, 1000000
s(i) = 1
enddo

do i=2, 1000000
if (s(i).eq.1) then
do j=2, (1000000/i)
s(i*j)=0
enddo
endif
enddo

do i=2, 1000000

if (s(i).eq.1) then
do j=1,sequence-1	
if (s(i+offset(j)).ne.1) goto 10
enddo
n=n+1
write(*,*) n, i,i+2,i+6,i+8
endif
10	continue
enddo


end

Thanks in advance.

---

### Post by ibuclaw on 2010-01-17
I get
```
1           3           5           9          11
```
Which correlates to: n, i,i+2,i+6,i+8
If n is supposed to be 1, and i is supposed 3 in this application.

Regards
Iain

---

### Post by TheStatsMan on 2010-01-17
Why don't you simply compile it and run it yourself. Save it as sieve.f90

Then
```

gfortran sieve.f90 -o sieve
./sieve

```

---

