---
title: "[C99] A question about malloc()"
date: 2014-01-23
forum: Programming Talk
---

### Post by ppplayer80 on 2014-01-23
Hi!

If I do something like this:
```
int *array = (int*) malloc(sizeof(int) * randomnumber);
```

Does it mean that malloc creates an... lets say 'continuous' block of memory for this array? I mean, when I do something like
```

int *var = array+1;
*var = 5;
```
Can i be sure that It won't explode and save 5 in my array?

---

### Post by ofnuts on 2014-01-23
[LIST]
[*]The block isn't created but allocated. This looks pedantic, but in some cases you have to remember that there is only so much memory to allocate.
[*]Do not cast the returned value of malloc(). malloc() returns a "void*", a pointer to anything that fits any typed pointer without a cast. When you cast you run the risk to not notice that you forgot to declare malloc() properly (because the compiler will think it returns an int, and with a cast it won't warn you about assigning the int to a pointer)
[*]Yes, the allocated block is continuous, so all pointers from the origin to the origin+allocated size-1(*) correspond to usable memory locations.
[/LIST]

(*) using the pointer arithmetic semantics, adding N to the pointer moves it (N * size_of_type_pointed_to) bytes.

---

### Post by Bachstelze on 2014-01-24
> **ppplayer80 said:**
> 
Can i be sure that It won't explode and save 5 in my array?

Yes... assuming randomnumber >= 2. ;)

---

