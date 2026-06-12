---
title: "Cmake not in path"
date: 2006-08-29
forum: Programming Talk
---

### Post by pihbar on 2006-08-29
I've been trying to set up wxMusik according to the [instructions from their website]("http://musik.berlios.de/?id=compileonlin").

When I do ccmake -DCMAKE_BUILD_TYPE:STRING=RelWithDebInfo ..

and press c to configure as in the instructions I get:
```
CMake Error: your C compiler: CMAKE_C_COMPILER_FULLPATH-NOTFOUND was not
 found in your path.   For CMake to correctly use try compile commands, the
 compiler must be in your path.   Please add the compiler to your PATH
 environment, and re-run CMake.

 CMake Error: Internal CMake error, TryCompile configure of cmake failed

 The C compiler "CMAKE_C_COMPILER_FULLPATH-NOTFOUND" is not able to compile a
 simple test program.
 It fails with the following output:


 CMake will not be able to correctly generate this project.

 CMake Error: your C compiler: CMAKE_C_COMPILER_FULLPATH-NOTFOUND was not
 found in your path.   For CMake to correctly use try compile commands, the
 compiler must be in your path.   Please add the compiler to your PATH
 environment, and re-run CMake.

```

I have cmake installed. Do I need to add somethign to the path?

---

### Post by mogelhead on 2006-08-30
It's the C compiler that is not in the path.

Have you installed GCC?

---

### Post by pihbar on 2006-08-30
](*,) 

now i did. solved. thanks.

---

