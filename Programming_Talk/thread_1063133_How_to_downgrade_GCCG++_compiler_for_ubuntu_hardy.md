---
title: "How to downgrade GCC/G++ compiler for ubuntu hardy"
date: 2009-02-07
forum: Programming Talk
---

### Post by remy06 on 2009-02-07
Hello.

I am working on a programming assignment that requires me to compile my C/C++ code using only GCC/G++ 4.0 and ubuntu hardy.

I've found that hardy has 4.2.3 version installed therefore I will need to downgrade it.

Is it possible to do so in hardy?If so,will appreciate some advice on how do I go about installing GCC/G++ 4.0(able to install through apt-get?) and compile using it?

As the submission deadline is near,I've started coding it and am looking forward to hear from you guys.

Thanks in advance

---

### Post by hessiess on 2009-02-07
Just use the newer version, it is unlickly to make much differance.

---

### Post by dribeas on 2009-02-07
> **remy06 said:**
> 
Is it possible to do so in hardy?If so,will appreciate some advice on how do I go about installing GCC/G++ 4.0(able to install through apt-get?) and compile using it?


You can install the gcc/g++ 4.0 side by side with the current 4.2 version with just apt-get. You will have to modify your building scripts to use the older version as g++ will default to the latest version.

If you use makefiles (and if it does not manually set the compiler) you will be able to determine the computer to use with CC / CXX environment variables. I use cmake, in that case you will have to define the CXX variable _before_ running cmake (and after cleaning CMakeCache.txt from the root build directory). With other build tools you will have to find out on your own.

```

# cmake
project-root$ rm CMakeCache.txt
project-root$ CXX=g++-4.0 cmake .
project-root$ make

# makefile
project-root$ CXX=g++-4.0 make 

```

If you want it for a longer time you can set it in .bashrc:

```

#somewhere inside .bashrc

export CXX=g++-4.0

```

In that case you will have to close and reopen the terminal for the new setting to apply.

---

### Post by snova on 2009-02-07
> **remy06 said:**
> I am working on a programming assignment that requires me to compile my C/C++ code using only GCC/G++ 4.0 and ubuntu hardy.

I've found that hardy has 4.2.3 version installed therefore I will need to downgrade it.

I sincerely doubt you need to do anything. When they say "4.0", much of the time that does *not* refer to one, single specific release, but to the entire series. In this case, the 4.x series.

I can't imagine why he would require you to use an outdated version.

---

### Post by happysmileman on 2009-02-07
> **snova said:**
> I sincerely doubt you need to do anything. When they say "4.0", much of the time that does *not* refer to one, single specific release, but to the entire series. In this case, the 4.x series.

I can't imagine why he would require you to use an outdated version.

I imagine you're right, and even if not anything written for 4.2.3 will almost definitely compile on 4.0, but unless he gets clarification I guess he doesn't want to take a risk, however small.

---

