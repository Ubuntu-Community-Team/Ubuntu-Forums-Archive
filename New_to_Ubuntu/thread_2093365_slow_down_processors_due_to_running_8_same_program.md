---
title: "slow down processors due to running 8 same programs in 8 cores simultaneously"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by alireza2010 on 2012-12-10
I have a  computer with 2 intel xeon 4-core processors and 2.0 GHz speed (it means I have 8 cores on my computer). when I  run a program it takes about 33 seconds. but when I run 8 programs (same  programs) simultaneously in 8 different folders, they take about 120  seconds each. I'm so confused. what's the problem?
I use Ubuntu 11.04. I also used the CENT OS 5. but it had the same problem.
for check this problem I checked another sample FORTRAN code that does not need huge memory and I/O. My sample code is:

     ```
program testcpuspeed
implicit none
integer i,j,k
integer,parameter::n=1000000
real(8) a(n),b(n),r


do i=1,1000

    do j=1,n
        a(j)=3321.312+1.0/(float(i)+54.4545)
        b(j)=15.0-1.0/(float(i)+400.055)
    end do

    do k=1+100,n-100
        a(k)=a(k)+21.313+b(k-100)+b(k+100)
    end do

    r=dot_product(a,b)
end do

print*,r

end program testcpuspeed                      
```You can compile it with "gfortran -O3 filename.f90 -o exe"
The output will be "exe"
You can test the time with 
```
time ./exe
```for 1 core. and 
```
time ./exe  & 
time ./exe & 
time ./exe &
time ./exe & 
time ./exe  & 
time ./exe & 
time ./exe & 
time ./exe &

```for 8 cores.
In my computer it take about 13 sec for 1 core and about 50 sec for 8 cores. it means my computer uses only of 2 core effectively. when I get top during running with 8 cores I have 8 thread with 100% capacity which means all 8 cores are running my programs. 

I checked it with another computer. Running this program with 1 core does not differ from 8 core alot in that computer.
you can check this program in your laptop and check the difference. the number of "time ./exe & " should be as same as your number of your real cores.

---

### Post by lisati on 2012-12-10
Thread closed, duplicate of [http://ubuntuforums.org/showthread.php?t=2092018](http://ubuntuforums.org/showthread.php?t=2092018)

---

