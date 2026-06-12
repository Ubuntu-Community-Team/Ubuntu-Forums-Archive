---
title: "Developing MPI programs in Eclipse"
date: 2011-04-21
forum: Programming Talk
---

### Post by Moohasha on 2011-04-21
I've played around with writing simple MPI programs in C, but now I'm trying to do something a little more complex in C++.  I'm using Eclipse, but I keep getting compile errors when I try to compile.

I'm using MPICH2 and I've modified my project properties to use mpicc for the compiler.  My code is very simple:

```
#include <iostream>
#include "mpi.h"

int main(int argc, char** argv)
{
	MPI::Init(&argc, &argv);
	std::cout << "!!!Hello World!!!" << std::endl;
	MPI::Finalize();
	return 0;
}
```

Yet when I try to build I get the following errors:

> 
**** Build of configuration Debug for project CppTesting ****

make all 
Building file: ../src/CppTesting.cpp
Invoking: GCC C++ Compiler
mpicc -I/usr/include/mpi -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/CppTesting.d" -MT"src/CppTesting.d" -o"src/CppTesting.o" "../src/CppTesting.cpp"
../src/CppTesting.cpp: In function ‘int main(int, char**)’:
../src/CppTesting.cpp:14: error: no matching function for call to ‘Init(int*, char***)’
/usr/include/mpi/mpicxx.h:2697: note: candidates are: void MPI::Init()
/usr/include/mpi/mpicxx.h:2698: note:                 void MPI::Init(int&, char**&)
make: *** [src/CppTesting.o] Error 1

Does anyone have any suggestions?

---

### Post by Some Penguin on 2011-04-21
Re-read the error message, as it contains quite enough information.

---

### Post by schauerlich on 2011-04-22
> **Some Penguin said:**
> Re-read the error message, as it contains quite enough information.

I'll even narrow it down for you:

> ../src/CppTesting.cpp:14: error: no matching function for call to ‘Init(int*, char***)’
/usr/include/mpi/mpicxx.h:2697: note: candidates are: void MPI::Init()
/usr/include/mpi/mpicxx.h:2698: note: void MPI::Init(int&, char**&)

---

### Post by Moohasha on 2011-04-22
Yeah, it was really late when I posted that.  I fixed that really n00b bug and am getting the errors I MEANT to post originally.  I'm on a different machine now, so I'll post that later...

---

### Post by Moohasha on 2011-04-25
Ok, this is what I meant.  As stated previously, I'm using the mpicc compiler (I've also tried with mpic++ and got the same error).  I added /usr/include/mpi to the include paths, but I'm getting this error:

```
**** Build of configuration Debug for project CppTesting ****

make all 
Building target: CppTesting
Invoking: GCC C++ Linker
g++ -fopenmp -o"CppTesting"  ./src/CppTesting.o   
./src/CppTesting.o: In function `main':
/home/david/workspace/CppTesting/Debug/../src/CppTesting.cpp:14: undefined reference to `MPI::Init(int&, char**&)'
/home/david/workspace/CppTesting/Debug/../src/CppTesting.cpp:16: undefined reference to `MPI::Finalize()'
collect2: ld returned 1 exit status
make: *** [CppTesting] Error
```

I feel like I'm missing something simple.

---

### Post by talonmies on 2011-04-26
> **Moohasha said:**
> I feel like I'm missing something simple.
You are: the mpi libraries. Either link with mpicxx or explicitly add the MPI libraries to the link statement.

---

### Post by Moohasha on 2011-04-27
Ah, I missed that those were link errors.  I'm used to programming in Visual Studio where link errors look very different.  I tried setting mpic++ as the linker tool (it was still set to g++) and specifically adding the path to the mpi libraries (/usr/lib), but that didn't change anything.

If I just run mpic++ from the terminal it builds and links just fine.  It's just a pain having to switch back and forth, which is why I'm using an IDE in the first place. =P

---

