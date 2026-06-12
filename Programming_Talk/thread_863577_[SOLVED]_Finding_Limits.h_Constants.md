---
title: "[SOLVED] Finding Limits.h Constants"
date: 2008-07-18
forum: Programming Talk
---

### Post by British0zzy on 2008-07-18
I wrote this program to find the Maximums and Minimums of the constants in the Limits.h header.
Here's the code:
```
#include <stdio.h>
#include <limits.h>

main()
{
    printf("Bits in a char: %+d\n", CHAR_BIT);
    printf("Unsigned Character Max: %+d\n", UCHAR_MAX);
    printf("Unsigned Character Minimum: 0\n");
    printf("Signed Character Maximum: %+d\n", SCHAR_MAX);
    printf("Signed Character Minimum: %+d\n", SCHAR_MIN);
    printf("Unsigned Integer Maximum: %+ld\n", UINT_MAX);
    printf("Unsigned Integer Minimum: 0\n");
    printf("Signed Interger Max: %+d\n", INT_MAX);
    printf("Signed Integer Minimum: %+d\n", INT_MIN);
    printf("Unsigned Short Maximum: %+d\n", USHRT_MAX);
    printf("Unsigned Short Minimum: 0\n");
    printf("Signed Short Maximum: %+d\n", SHRT_MAX);
    printf("Signed Short Minimum: %+d\n", SHRT_MIN);
    printf("Unsigned Long Maximum: %+lld\n", ULONG_MAX);
    printf("Unsigned Long Minimum: 0\n");
    printf("Signed Long Maximum: %+ld\n", LONG_MAX);
    printf("Signed Long Minimum: %+ld\n", LONG_MIN);
}
```

When I run the program here is the output:
```
Bits in a char: +8
Unsigned Character Max: +255
Unsigned Character Minimum: 0
Signed Character Maximum: +127
Signed Character Minimum: -128
Unsigned Integer Maximum: -1
Unsigned Integer Minimum: 0
Signed Interger Max: +2147483647
Signed Integer Minimum: -2147483648
Unsigned Short Maximum: +65535
Unsigned Short Minimum: 0
Signed Short Maximum: +32767
Signed Short Minimum: -32768
Unsigned Long Maximum: -8079434315340972033
Unsigned Long Minimum: 0
Signed Long Maximum: +2147483647
Signed Long Minimum: -2147483648

```

I am running this on a MacBook Pro with OSX 10.5.4 (I know... not Ubuntu)
Any thoughts?

---

### Post by Can+~ on 2008-07-18
How about..

[PHP]int main()
{
    ...
    reutrn 0;
}[/PHP]

Aside from that.. there isn't much to discuss, as it's just a trivial print constants.

---

### Post by WW on 2008-07-18
Use %u for unsigned integers.

---

### Post by British0zzy on 2008-07-18
> **Can+~ said:**
> there isn't much to discuss, as it's just a trivial print constants.

Could you explain or point me to a place that explains what these trivial print constants are??

Thanks WW, why doesn't a long work? From what I understand, as long as the print conversion can handle bigger numbers, it is ok to use it. For example I could use %+ld for CHAR_MAX. Is that wrong?

---

### Post by WW on 2008-07-18
> **British0zzy said:**
> 
Thanks WW, why doesn't a long work? From what I understand, as long as the print conversion can handle bigger numbers, it is ok to use it. For example I could use %+ld for CHAR_MAX. Is that wrong?
Sorry, my answer was too terse.  Use **u** (along with all the usual modifiers) instead of **d** if the argument is some form of unsigned integer.  E.g. %+u, %+lu, etc.

Notice that some of your "max unsigned" values are being printed as negative numbers.  Using **u** instead of **d** will fix that, and give you the correct values.

---

### Post by British0zzy on 2008-07-18
Thanks! That's what I was looking for. It's so hard to find these nuances even after reading about print conversions over and over :)

---

### Post by Can+~ on 2008-07-18
> **British0zzy said:**
> Could you explain or point me to a place that explains what these trivial print constants are??

Sorry if I sounded rude. The thing is that, those numbers are constants defined inside the library <[limits.h]("http://www.cplusplus.com/reference/clibrary/climits/")> and your code basically prints them. Constants is data that doesn't change, and printing is the printf function.

If this is your first C app, then it's ok, you should follow the tips above, use int main and return 0 as a convention.

---

### Post by mssever on 2008-07-18
> **British0zzy said:**
> ```
Unsigned Integer Maximum: -1
Unsigned Integer Minimum: 0
```
Are you sure this is correct? Aren't these lines mutually exclusive?

---

