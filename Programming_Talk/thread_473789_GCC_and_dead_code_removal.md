---
title: "GCC and dead code removal"
date: 2007-06-14
forum: Programming Talk
---

### Post by tomane on 2007-06-14
Hi

I was fiddling with a port of gcc for microblaze and optimization levels seeing if it removes code chunks that are never called. However, even with -O3 or -Os, I can find functions that are never called in the dump of the executable.

My code looks like this:

```

int main(void)
{
    while(1) {
        foo();
        continue;
        bar();
    }
}
```That continue is unconditional and it is only there for a couple tests I'm performing. Looking through the objdump -d, I can still find the code for `bar()`, although it will not be called one single time.

The microblaze gcc port is derived from gcc3.4.1, so if anyone has info on this, could you please tell me how to enable dead code removal with this gcc version, or even if this it, at all, suported.

Thanks,
cheers,
--to

---

### Post by meatpan on 2007-06-14
I tried to reproduce your experiment with:
Intel compiler: icc (ICC) 9.1 
GNU compiler: gcc (GCC) 3.4.6
GNU compiler: gcc4 (GCC) 4.1.1

The code I used:
```

void foo() {return;}
void bar() {return;}

int main(void)
{
    while(1) {
        foo();
        continue;
        bar();
    }
}


```

When running gcc -O3 test.c, and I found objdump -t (and objdump -d) contained bar.  gcc4 -O3 also had bar.
Howerver, icc -fast test.c, did not contain foo, or bar.  I think aggressive optimization by icc  *might* have been smart enough to remove the functions because they are just no-ops.

That said, I changed bar to contain a block of operations:
```

#include <stdio.h>

void foo() {return;}
void bar() {printf("Hello, world.\n"); return;}

int main(void)
{
    while(1) {
        foo();
        continue;
        bar();
    }
}

```

The resulting compilation via, icc -fast test.c, still did not contain bar.

Hope this helps.

---

### Post by tomane on 2007-06-14
Thanks for your post, meatpan. I tried your test.c with gcc-4.1.2 and gcc-3.4.6 -Os and bar still made it into the binary :(
Is dead code removal not as effective as ond would like it to be or must it be activated somehow to be performed in a more agressive way?

cheers,
--to

---

### Post by meatpan on 2007-06-14
I really have no idea :(

I took another glance at the gcc optimization options, and could not find anything that seemed to address this form of optimization.

The intel compiler is known to be a bit more aggressive, but I'm still surprised that gcc didn't remove the dead code.  There must be some sort of opt flag or param that we are missing.  Perhaps the gcc message boards would be able to give some better advice.

---

