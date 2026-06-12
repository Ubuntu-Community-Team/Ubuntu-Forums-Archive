---
title: "[SOLVED] [C] Bit manipulation ... Am I doing this right?"
date: 2008-12-29
forum: Programming Talk
---

### Post by OutOfReach on 2008-12-29
I have just finished a chapter in my book about bit operations, I am somewhat understanding the operators.
I am stuck on an exercise at the end of this chapter.

I am supposed to create a function named bit_test(), that tests a certain bit in the word if it is on or off. Easy right? Well not so much for me, I'm new to all this binary hexadecimal stuff.
Here's what I scraped up so far:
```

#include <stdio.h>

int bit_test(unsigned int source, int n);

int main(void)
{
    printf("%i\n", bit_test(0xabcdef00u, 1));
    return 0;
}

int bit_test(unsigned int source, int n)
{
    unsigned int index = source & ~(1 << n);

    if (index & 1)
    {
        return 1;
    }

    return 0;
}

```

source is of course the source byte, and n is the bit number.
No matter how much I change n, it still comes out 0.

Can someone please care to explain/help me with this? Thanks.

---

### Post by catchmeifyoutry on 2008-12-29
> **OutOfReach said:**
> 
```

#include <stdio.h>

int bit_test(unsigned int source, int n);

int main(void)
{
    printf("%i\n", bit_test(0xabcdef00u, 1));
    return 0;
}

int bit_test(unsigned int source, int n)
{
    unsigned int index = source & ~(1 << n);

    if (index & 1)
    {
        return 1;
    }

    return 0;
}

```


Hai, you create a bitmask with (1 << n), right, so in case of a single byte and n = 3 something like 00000100. You want to test if the bit in
source in that location is also 1, but in your post you invert the bitmask for some reason: 11111011. In your code after applying the bitwise & operator you can be sure that the n'th bit in index will always be 0! The other bits will be whatever they were in source. Continuing, you compare index with 00000001 "one" using &, so the result depends on only the last bit of index which is the last bit of source, me thinks.

Solution: apply the mask 00000100 directly on source such that the result only depends on the n'th bit in source:
```

(source & (1 << n))

```
This will return zero if the n'th bit in source was 0, and something non-zero if the bit was 1.

---

### Post by slavik on 2008-12-29
int n = ...; // bits to check
int x = ...; // bit place to check (with 0 being the ones place)

int check(int n, int x) {
  if ((n>>x) & 1) return 1;
  return 0;
}

---

### Post by anubhavrocks on 2008-12-29
Suppose you have:

value = 0xabcdef00
value = 1010 1011 1100 1101 1110 1111 0000 0000 binary

Now if you need to check if bit 8 is set or not you can AND "value" with 

(1<<8) .Using this we can now code.

so now: 

int bit_test(unsigned int source, int n)
{
  return (source & (1<<n));
}

---

### Post by catchmeifyoutry on 2008-12-29
> **slavik said:**
> int n = ...; // bits to check
int x = ...; // bit place to check (with 0 being the ones place)

int check(int n, int x) {
  if ((n>>x) & 1) return 1;
  return 0;
}

Well in that case, to stay close to the original post:
[PHP]
int bit_test(unsigned int source, int n)
{
    if (source & (1 << n))
        return 1;
    return 0;
}
[/PHP]

haha!:P

---

### Post by OutOfReach on 2008-12-29
Ahh, so the ones complement was unnecessary...

Thanks guys this stuff is starting to make more sense now (especially with catchmeifyoutry's explanation).

---

### Post by pokerbirch on 2008-12-29
There's a nice page of bit hacking stuff [HERE]("http://graphics.stanford.edu/~seander/bithacks.html") that i often refer to. If you like bit manipulation, you should try writing some poker evaluation code. It keeps you on your toes and teaches you how to optimize. ;)

---

