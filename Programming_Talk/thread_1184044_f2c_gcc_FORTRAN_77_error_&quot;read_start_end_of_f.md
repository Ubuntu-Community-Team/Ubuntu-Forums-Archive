---
title: "f2c gcc FORTRAN 77 error: &quot;read start: end of file&quot;"
date: 2009-06-10
forum: Programming Talk
---

### Post by newagelink on 2009-06-10
Using f2c, I compile FORTRAN 77 code using gcc. I receive the following error when attempting to execute the a.out file: > daniel@daniel-laptop:~/Documents/UCF$ ./a.out
read start: end of file
apparent state: unit 12 named coordinates.dat
last format: list io
lately reading sequential formatted external IO
Aborted I am completely new to FORTRAN 77. I think the problem is that it tries to read the *end* of coordinates.dat (which is, of course, blank), instead of its beginning. How do I get the READ command to read from the *beginning* of the file? Relevant code (I have inserted [...] to signify omitted code): ```
[...]
open(12,file='coordinates.dat')
write(12,*)'boxl=',boxl
[...]
write(12,*)'ith    rx       ry        rz'
do i=1,npart
  write(12,*)i,rx(i)/boxl,ry(i)/boxl,rz(i)/boxl
end do
[...]
write(12,*)'The particles begin moving:'
write(12,*)'i kstep rx(i,kstep) ry(i,kstep) rz(i,kstep)'
[...]
if ( mod(kstep,counter) .eq. 0) then
  write(12,*)i,kstep,rx(i),ry(i),rz(i)
end if
[...]
        REWIND(12)
        READ(12,*,END=99)
   99   CONTINUE
[...]
``` I preserved spacing only for the final statements, to show that I have placed the 99 label in columns four and five; the statements begin in the ninth column. Replacing the number '99' with '17' results in the same error, so I doubt it is reserved by anything.

I think that final READ statement produces the error; it is meant only to skip the first line of coordinates.dat: I do not know how to begin reading precisely where I want in the file. (If you could tell me, that would be great!)

Here is an abbreviated copy/paste of coordinates.dat's contents:  ```
boxl=  5.53760805
 ith    rx       ry        rz
 1  .23815977 -.049614668 -.229849831
 2  .280181556 -.224229727  .057457935
 3  .380852279 -.109275564  .322192416
[...]
 108 -.211492997  .098967771  .494598392
 The particles begin moving:
 i kstep rx(i,kstep) ry(i,kstep) rz(i,kstep)
 1 5  1.34882447 -.308069657 -1.27918501
 2 5  1.59313361 -1.21831491  .364117496
 3 5  2.10201027 -.594138058  1.69803586
[...]
 108 10 -1.04466499  .694539981  2.69455404
[...]
 108 15 -.944414731  .705275409  2.66779623
[...]
 108 500 -.590130643 -.236264398  2.43655859
``` I am using FORTRAN 77, rather than the newest version, because I think my professor requires it; see [my question concerning compilers]("http://ubuntuforums.org/showthread.php?t=1183889"). I hope using f2c and gcc is not a bad idea; I would like to become a better programmer to use gfortran (knowing it compiles as FORTRAN 95), but I must tackle this error first.

Thanks!

*18:51 EST update*: I changed the final code shown above to the following: ```
	REWIND(12,ERR=99)
   99   PRINT 'REWIND failed!'
	READ(12,*,END=17)dummy
   17   PRINT 'READ failed!'
``` The new error messages, although the code compiles without an error: > daniel@daniel-laptop:~/Documents/UCF$ ./a.out
startio: error in format
apparent state: unit 6 (unnamed)
last format: REWIND failed!
lately writing sequential formatted external IO
Aborted

*11 June 10:05 Update*:
With the following code, I am no longer receiving any run-time error:
```
	REWIND 12
	READ(12,*)
	READ(12,*)	
	do j = 1,npart
	  READ(12,*) i,rxs(i),rys(i),rzs(i)
	end do
``` The REWIND statement was apparently the solution, so that it was reading from the top of the file, rather than the end. :) Thanks, #fortran on FreeNode.

---

