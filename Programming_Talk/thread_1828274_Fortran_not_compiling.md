---
title: "Fortran not compiling"
date: 2011-08-18
forum: Programming Talk
---

### Post by MG&amp;TL on 2011-08-18
Hi,
I am trying to compile a code in fortran 90(I am using gfortran compiler) but I get this error:"Error: Unclassified statement at <1>" This error is on the line 11. The 1 is under the first 'Te'. The code is attached. I wrote the code in windows but have tried to compile it in windows and Edubuntu getting the same error messages. Other codes written in Edubuntu have compiled fine in both so it isn't a bug in the compiler.
Any help as to why my code won't compile will be much appreciated:)
MG

---

### Post by Queue29 on 2011-08-18
You have a parenthesis mismatch (missing an opening parenthesis!)

---

### Post by cgroza on 2011-08-18
Post your code in CODE tags. Not everyone is willing to download a file to help.

---

### Post by MG&amp;TL on 2011-08-18
Thanks Queue29. That sorted out the problem.:D
Thanks for the comment cgroza, I'll bear that in mind next time.

---

### Post by MG&amp;TL on 2011-08-19
Hi, after realizing I had made an error in the equation, I changed the equation. When I tried to recompile I got the same error message at the same place as last time but I've checked for parenthesis mismatches and there aren't any.
Heres the code:
```
program heat
implicit none
integer:: iterations
real:: k,time,step,R,T0,Te
write(*,*) 'Please enter the ambient temperature, constant of proportinality,'
write(*,*)'the intial temperature of the object ,the time at which you want to know the temperature of the body' 
write(*,*)'and the size of the step in time units to use in the Euler method.'
read(*,*)R, k, T0, time, step
Te=T0
do iterations=0,nint((1/step)*time), 1
Te+=(((k*(R-Te))/step)
end do
write(*,*)'The Temperature is',Te
stop
end program heat
```
Any further help will be much appreciated.
MG

---

### Post by Smart Viking on 2011-08-19
I don't really know fortran but.
```
Te+=(((k*(R-Te))/step)

```To me that looks very much like a parentheses mismatch.

---

### Post by MG&amp;TL on 2011-08-19
Oh yes, it is. Thanks very much Smart Viking:D:D . I'll try that.
MG

---

### Post by MG&amp;TL on 2011-08-19
That hasn't made any change unfortunately.:(
MG

---

### Post by Smart Viking on 2011-08-19
This works for me:
```
program heat
implicit none
integer:: iterations
real:: k,time,step,R,T0,Te
write(*,*) 'Please enter the ambient temperature, constant of proportinality,'
write(*,*)'the intial temperature of the object ,the time at which you want to know the temperature of the body'
write(*,*)'and the size of the step in time units to use in the Euler method.'
read(*,*)R, k, T0, time, step
Te=T0
do iterations=0,nint((1/step)*time), 1
Te=Te+((k*(R-Te))/step)
end do
write(*,*)'The Temperature is',Te
stop
end program heat


```I saved it as file.f90, and compiled it with "gfortran file.f90".
I'm not sure if that's the correct equation you want.

---

### Post by MG&amp;TL on 2011-08-19
Yes, thats the correct equation. I can't see why it doesn't compile on mine but does on yours.

---

### Post by Smart Viking on 2011-08-19
It is important that the file ends with ".f90", otherwise gfortran wont compile it as fortran 90.

---

### Post by MG&amp;TL on 2011-08-19
Yes, I do that but I use a slightly different way of compiling to you. I use 
```
gfortran -o Newton Newton.f90
``` in this case.

MG

---

### Post by Smart Viking on 2011-08-19
That's weird. 
Output from gfortran -v:
```
$ gfortran -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.3-4ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-plugin --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 

```

Added the executable as an attachment.

---

### Post by MG&amp;TL on 2011-08-19
Thanks for sending the .gz over but apparently my virtual box edubuntu doesn't have any applications to open .exes. I tried through terminal but I got permission denied, when I run it as root I get 'command not found'. This may be due to the fact that my virtual box has been playing up.

MG

---

### Post by Smart Viking on 2011-08-19
The .gz means it's compressed, this is what you do:
```
gzip -d Newton.gz
chmod +x Newton
./Newton
```

---

### Post by Queue29 on 2011-08-19
Fortran does not have a **+=** operator. You gotta rewrite the equation without it.

---

### Post by MG&amp;TL on 2011-08-19
Thanks a lot!:) I had forgotten the chmod +x Newton bit. The executable works fine.

---

### Post by MG&amp;TL on 2011-08-19
Thanks Queue29, I'll rewrite the equation with out +=.
Thanks to all of you who have responded.It Now compiles fine:D

---

