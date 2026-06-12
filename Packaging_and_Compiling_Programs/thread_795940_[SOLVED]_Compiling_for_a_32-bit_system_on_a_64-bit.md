---
title: "[SOLVED] Compiling for a 32-bit system on a 64-bit Ubuntu"
date: 2008-05-15
forum: Packaging and Compiling Programs
---

### Post by yang on 2008-05-15
Hi, I'm trying to build a program ([xoc]("http://pdos.csail.mit.edu/xoc/")) that targets a 32-bit environment (I'm on 64-bit Ubuntu), but I get the error below.

```

$ make zeta/zeta
...
g++ -m32 -lrt -o zeta obj/ast1.o obj/builtin.o obj/debug.o obj/code.o obj/compile.o obj/constant.o obj/disasm.o obj/expr.o obj/gc.o obj/grammar.o obj/grammarbuild.o obj/grammarparse.o obj/grammarstruct.o obj/grammartyping.o obj/iterate.o obj/lex1.o obj/main.o obj/pattern.o obj/pprint.o obj/profile.o obj/run.o obj/stmt.o obj/type.o obj/typecheck.o obj/y.tab.o  obj/arena.o obj/bitset.o obj/cfg-comp.o obj/cfg-gram.o obj/cfg-rule.o obj/cfg-sym.o obj/dfa.o obj/emalloc.o obj/error.o obj/errstr.o obj/gflags.o obj/glr-parse.o obj/hash1.o obj/line.o obj/name.o obj/nfa.o obj/panic.o obj/regexp9.o obj/slr-state.o obj/slr-comp.o obj/slr-parse.o obj/slr-dump.o obj/libfmt.a obj/libutf.a  -lm
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status
make[1]: *** [zeta] Error 1
make[1]: Leaving directory `/tmp/xoc-asplos/zeta'
make: *** [zeta/zeta] Error 2

```

I then tried building a hello-world program with g++ -m32, and I still get the error:

```
/usr/bin/ld: cannot find -lstdc++
```

I notice that the libstdc++ libraries do include *something* 32-bit...

```

$ dpkg -L libstdc++6-4.2-dev|grep 32
/usr/include/c++/4.2/x86_64-linux-gnu/32

```

I also tried everything with linux32 but that made no difference.  Any hints?  Thanks in advance!

---

### Post by zenwalker on 2008-05-16
Well u have a 64 bit package of C++ libs i belive, coz the package name X86_64 says it. Althought a wild guess ;)

---

### Post by yang on 2008-05-16
Yeah, sorry I forgot to explicitly mention that I am on a 64-bit system.

---

### Post by yang on 2008-05-16
I fixed this issue by installing the g++-multilib package.

---

