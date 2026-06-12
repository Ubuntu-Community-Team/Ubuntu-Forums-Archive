---
title: "why an empty Structure....."
date: 2009-02-02
forum: Programming Talk
---

### Post by kim.wilzon on 2009-02-02
hi,

Please tell me why an empty Structure will occupy 2Bytes in C++ ?

Thanks

---

### Post by maximinus_uk on 2009-02-02
Your probably looking at the size of the pointer, rather than the size of a structure. Pointer being 32 bits, i.e. 2 bytes on a 32-bit machine.

---

### Post by Zugzwang on 2009-02-02
What is an empty structure? Is it something like this?

[PHP]
#include <iostream>

class Test {
};

int main() {
    std::cout << "Sizeof(Test): " << sizeof(Test) << "\n";
}
[/PHP]

---

### Post by Zugzwang on 2009-02-02
> **maximinus_uk said:**
> Your probably looking at the size of the pointer, rather than the size of a structure. Pointer being 32 bits, i.e. 2 bytes on a 32-bit machine.

No, that's 4 bytes. In fact, the 2 bytes thing looks rather incorrect. That might IMHO only be the case on some 16bit compilers with alignment enabled.

---

### Post by maximinus_uk on 2009-02-02
I hereby hand in my geek card. 32/8=4 :(

---

### Post by mdurham on 2009-02-02
It is curios indeed.

```

class Test {
    char x[0];
};

results in a size of 0 (zero)

class Test {
};

results in a size of 1

```

What's going on here? It can't be due to alignment as someone suggested because sizeof(something) just gives the size of err... something.

---

### Post by doojsdad on 2009-02-02
Looks like it has something to do with the fact that "no object shall have the same address in memory as any other variable". 

[http://bytes.com/topic/c/insights/660463-sizeof-empty-class-structure-1-a](http://bytes.com/topic/c/insights/660463-sizeof-empty-class-structure-1-a)

What compiler are you using?

---

### Post by Npl on 2009-02-02
sizeof on an Type/Class must be non-zero, its a requirement of C/C++ Standard.
sizeof on an Array can be zero.

---

### Post by mdurham on 2009-02-02
> **Npl said:**
> sizeof on an Type/Class must be non-zero, its a requirement of C/C++ Standard.
sizeof on an Array can be zero.

how do you explain this?
```
class Test {
    char x[0];
};


```sizeof(Test) results in a size of 0 (zero)

Using 64bit G++ in Jaunty

---

### Post by johnl on 2009-02-02
I tried compiling the same snippet -pedantic:

```

g++ test.cc -Wall -pedantic -o test
test.cc:6: error: ISO C++ forbids zero-size array `x`

```

It sounds to me like the ability to have a 0-sized structure is supported by g++ but not the C++ standard.

Compiling the following:
```

class Test {
};

```
with -pedantic resulted in sizeof(Test) == 1.

---

### Post by Npl on 2009-02-03
> **mdurham said:**
> how do you explain this?
```
class Test {
    char x[0];
};


```sizeof(Test) results in a size of 0 (zero)

Using 64bit G++ in JauntyCompilerbug?
Returns 1 on MSVC.

---

### Post by Zugzwang on 2009-02-03
> **Npl said:**
> Compilerbug?
Returns 1 on MSVC.

No. That's called undefined behaviour.

---

### Post by Npl on 2009-02-03
> **Zugzwang said:**
> No. That's called undefined behaviour.Do you agree that Test is a class, irregardless of its members?
```
class Test {
    char x[0];
};
```

The C++ Standard is very clear about classes having a size > 0.

[QUOTE=ISO/IEC 14882]When applied to a class, the result is the number of bytes in an object of that class including any padding required for placing objects of that type in an array. The size of a most derived class shall be greater than zero (1.8)[/QUOTE]

---

### Post by Zugzwang on 2009-02-03
> **Npl said:**
> The C++ Standard is very clear about classes having a size > 0.

Right, but it also does not allow arrays of size 0. Therefore, since the input isn't standard, the output does not need to be either.

---

### Post by Npl on 2009-02-03
> **Zugzwang said:**
> Right, but it also does not allow arrays of size 0. Therefore, since the input isn't standard, the output does not need to be either.Again, what do you think Test is, Is it a class or not?
Either zero-sized arrays are an **extension** which means they dont break other rules (or atleast note what rules they affect). Or we talking about intentionally breaking the whole C++-Standard.

The third option is the most likely - planned to be an extension but buggy.

---

