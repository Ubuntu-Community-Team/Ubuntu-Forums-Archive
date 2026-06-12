---
title: "How do I compile a 64-bit c++ prog using code blocks Ubuntu"
date: 2012-09-30
forum: Programming Talk
---

### Post by abubakarsiddique on 2012-09-30
Hi,
I  have a multithreaded c++ code, I am trying to compile it using code  blocks on 64-ubuntu, for 32-bit compilation I gave -m32 and it works  good but for 64-bit I gave -m64 and it failed. I am using   #elif defined(__ia64__) && defined(__GNUC__)
  it simply unable to recognize it.

---

### Post by 3Miro on 2012-09-30
If you are already using 64-bit system, then you don't need any special flags to compile the program for 64-bit. Remove the -m32 and don't add anything else, it should work.

---

### Post by abubakarsiddique on 2012-09-30
thanx for ur response, I have already tried it but same error,
  it simply unable to recognize " #elif defined(__ia64__) && defined(__GNUC__)"

---

### Post by spjackson on 2012-09-30
Are you saying that you expect __ia64__ to be defined but it isn't?
You won't get it if the target is x86_64.
```

uname -a
gcc -v

```You can dump predefined macros with
```

gcc -dM -E foo.c > foo.log

```

---

### Post by abubakarsiddique on 2012-09-30
> **spjackson said:**
> Are you saying that you expect __ia64__ to be defined but it isn't?
You won't get it if the target is x86_64.
```

uname -a
gcc -v

```You can dump predefined macros with
```

gcc -dM -E foo.c > foo.log

```

Boss you are right,  the target is x86_64, and i am expecting ia64. now can you please tell me the settings in code blocks or some thing else because i want to compile it at 
"_ia64  && GNUC" as target. tahnx for your +ve response

---

### Post by oldos2er on 2012-09-30
Moved to Programming Talk.

---

### Post by abubakarsiddique on 2012-09-30
Hi,
I  have a multithreaded c++ code, I am trying to compile it using code   blocks on 64-ubuntu, for 32-bit compilation I gave -m32 and it works   good but for 64-bit I gave -m64 and it failed. I am using   #elif  defined(__ia64__) && defined(__GNUC__)
  it simply unable to recognize it.
Infact I want to set its target compiler ia64 but it is x86_64, can any one guide me how can i change code blocks settings or some other solution for this problem.Thanx

Regards
AB

---

### Post by spjackson on 2012-10-01
As I understand it, if you are not on an ia64 platform, you need to install a cross-compiler and toolchain if you want to build ia64 executables. Then you will need to configure your IDE to use that toolchain. I do question the merit of cross-compiling in an IDE because you can't run the code or debug it. So what does the added compexity of configuring the IDE give you exactly?

---

