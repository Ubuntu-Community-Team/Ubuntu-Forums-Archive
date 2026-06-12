---
title: "error in gcov - `__gcov_init' is referenced by DSO"
date: 2012-11-19
forum: Programming Talk
---

### Post by IAMTubby on 2012-11-19
Hey,
I am suddenly getting an error when trying to compile my application with the gcov flags enabled.

This is how my makefile looks
```

CFLAGS+= -fprofile-arcs -ftest-coverage

$(LINK) $(LDFLAGS) $(OBJS) -o $@  $(LIBS) /home/myinternship/xsr_toolchain/ppc_4xx/usr/lib/gcc/ppc-linux/4.2.2/libgcov.a

```

None of the other lines have anything to do with gcov.

This is the error I get
```

/home/myinternship/xsr_toolchain/usr/bin/ppc_4xx-gcc -Wl,-L/home/xsr_open/lib -Wl,-rpath-link,/home/xsr_open/lib  --cref --warn-common main.o  -o racadm  -L/home/xsr_open/lib -lxsrcli /home/xsr_toolchain/ppc_4xx/usr/lib/gcc/ppc-linux/4.2.2/libgcov.a

/opt/xsr_toolchain-4.2/usr/bin/../lib/gcc/powerpc-linux/4.2.2/../../../../powerpc-linux/bin/ld: xsrcli: hidden symbol `__gcov_init' in /home/xsr_toolchain/ppc_4xx/usr/lib/gcc/ppc-linux/4.2.2/libgcov.a(_gcov.o) is referenced by DSO

/opt/xsr_toolchain-4.2/usr/bin/../lib/gcc/powerpc-linux/4.2.2/../../../../powerpc-linux/bin/ld: final link failed: Nonrepresentable section on output

collect2: ld returned 1 exit status

make: *** [xsrcli] Error 1

```

Please advise.
I'm actually surprised that everything WAS building sometime back and then without any code change, it just suddenly refuses to build.
For the error log, I have added a space in between for the purpose of readability.

---

### Post by IAMTubby on 2012-11-19
This link solved the error.

[http://stackoverflow.com/questions/566472/where-is-the-gcov-symbols](http://stackoverflow.com/questions/566472/where-is-the-gcov-symbols)

Thanks.
Marking the thread as solved.

But I still have no idea why everything just stopped working without any code change.

---

