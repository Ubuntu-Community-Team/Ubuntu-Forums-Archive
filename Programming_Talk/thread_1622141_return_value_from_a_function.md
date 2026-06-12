---
title: "return value from a function"
date: 2010-11-15
forum: Programming Talk
---

### Post by jamesbon on 2010-11-15
On this link [http://lxr.ncu.cc/source/kernel/timer.c#094](http://lxr.ncu.cc/source/kernel/timer.c#094) a return type is defined
```
     return ((unsigned int)(unsigned long)base & TBASE_DEFERRABLE_FLAG);

```
What is the above function returning.I am not clear with definition of what is being returned in the above code.

---

### Post by Tony Flury on 2010-11-15
I think it is returning an unsigned int.

the function declaration will tell you (assuming this is C/C++) : 

```

static inline unsigned int tbase_get_deferrable(struct tvec_base *base)

```

I think base is cast to an unsigned long and then cast to a unsigned int (presumably truncating it depending on the actual size of int and long) and then bitwise AND with TBASE_DEFERRABLE_FLAG, so it will return either a zero or non-zero value depending if that flag is unset or set.

---

### Post by jamesbon on 2010-11-15
Is the same thing happening here
[http://www.mjmwired.net/kernel/Documentation/prctl/disable-tsc-ctxt-sw-stress-test.c#34](http://www.mjmwired.net/kernel/Documentation/prctl/disable-tsc-ctxt-sw-stress-test.c#34)

---

### Post by worksofcraft on 2010-11-15
[php]
#define TBASE_DEFERRABLE_FLAG           (0x1)
/* Functions below help us manage 'deferrable' flag */
static inline unsigned int tbase_get_deferrable(struct tvec_base *base)
{
         return ((unsigned int)(unsigned long)base & TBASE_DEFERRABLE_FLAG);
}
[/php]

Sheesh... :shock: it's really not a good example to learn from IMHO what are you hoping to gain from reading that?

---

### Post by nvteighen on 2010-11-16
That's highly optimized C... as I would expect from the Linux kernel source... There are a couple of things going on there: using bitmasking as a way to express stuff and then two castings that I guess/hope mainpulate the result of the bitmask in such a way that it's useful. I'm not a kernel hacker, so I can't tell you what the hell is going on there, but what I can tell you is that, if interested in reading others' source code, you should rather take a look to applications written in C and not the kernel.

---

