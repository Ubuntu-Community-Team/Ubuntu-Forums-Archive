---
title: "C++ functions returning pointers help."
date: 2009-03-11
forum: Programming Talk
---

### Post by jacensolo on 2009-03-11
FYI: I'm not new to programming, just having trouble understanding a couple things.

I've started to use Irrlicht (which is really nice btw) and am creating a couple demos for myself. I've done other C++ projects and have always stumbled on how, but understood that it worked and just did it. Finally, seeing that irrlicht does this, I want to know why.

Quite a few functions in Irrlicht return pointers. Why? How?
example:
```
IrrlichtDevice *device = createDevice(blahblahblah)
```

From my understanding, anything in in a function is destroyed at the end of the function, so what is device pointing to? 


But since it does seem to work for some reason, why make this a pointer? What's wrong with passing this by value?

I have dealt with this before and just gone with the flow, but I feel I should probably understand it.

---

### Post by scourge on 2009-03-11
> From my understanding, anything in in a function is destroyed at the end of the function, so what is device pointing to?

You're thinking of statically allocated stuff, which is deleted at the end of the block (not necessarily a function). Dynamically allocated objects stay alive until you manually delete them.


> But since it does seem to work for some reason, why make this a pointer? What's wrong with passing this by value?

Passing a complex object by value means that the object has to be copied, which is slow. And often you actually want access to a specific object, not just a copy of it. In C++ references are preferred, but they have some limitations that pointers don't have.

---

### Post by jacensolo on 2009-03-11
I thought dynamically allocated memory used the new keyword. The above example does not.

---

### Post by snova on 2009-03-11
> **jacensolo said:**
> I thought dynamically allocated memory used the new keyword. The above example does not.

But it's not allocating anything; the function you call is. Then it returns a pointer to that allocated memory, which you **delete** when you're done with.

---

### Post by dwhitney67 on 2009-03-11
@ OP

Does this make sense?
```

IrrlichtDevice* createDevice(...)
{
  IrrlichtDevice* d = new IrrlichtDevice(...);

  ...

  return d;
}

...

IrrlichtDevice* device = createDevice(...);

...

delete device;

```

---

### Post by jacensolo on 2009-03-11
> **dwhitney67 said:**
> @ OP

Does this make sense?
```

IrrlichtDevice* createDevice(...)
{
  IrrlichtDevice* d = new IrrlichtDevice(...);

  ...

  return d;
}

...

IrrlichtDevice* device = createDevice(...);

...

delete device;

```


That makes plenty of sense. Thanks :D

---

