---
title: "gcc compilation time"
date: 2008-01-26
forum: Programming Talk
---

### Post by hanniph on 2008-01-26
I'm using gcc for my programs written in c++ and I need to obtain compilation time result.
Is there any option of doing it?

---

### Post by Jessehk on 2008-01-26
I'm confused. Do you want to know the amount of time a compile takes,  or do you want to calculate a value during compile time (template-metaprogramming)?

In either case:
```

#include <iostream>

template <int N>
class Factorial {
public:
    enum { value = N * Factorial<N - 1>::value };
};

template <>
class Factorial<0> {
public:
    enum { value = 1 };
};

int main() {
    std::cout << Factorial<0>::value << std::endl;
    std::cout << Factorial<6>::value << std::endl;
}

```

```

$ time g++ -Wall -Wextra example.cpp -o example

real	0m0.476s
user	0m0.437s
sys	0m0.027s
$ ./example 
1
720

```

---

### Post by hanniph on 2008-01-26
> **Jessehk said:**
> I'm confused. Do you want to know the amount of time a compile takes,  or do you want to calculate a value during compile time (template-metaprogramming)?



I needed the amount of time that compile takes. thanks

---

### Post by scruff on 2008-01-26
This will get you time in seconds:

```

# START=`date +%s`; (put g++ stuff here) ; FINISH=`date +%s`; let TIME=$(( $FINISH-$START )); echo $TIME

```

---

### Post by LaRoza on 2008-01-26
Also, be aware that it isn't just compiling, it is preprocessing, compiling to assembly, assembling (which is a funny word to say), and linking.

---

