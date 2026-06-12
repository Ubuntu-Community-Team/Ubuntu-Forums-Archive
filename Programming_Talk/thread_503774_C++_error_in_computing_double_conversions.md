---
title: "C++: error in computing double conversions"
date: 2007-07-18
forum: Programming Talk
---

### Post by codatore on 2007-07-18
Hi all,

please consider the following very simple C/C++ code:

[FONT="Courier New"]#include <stdio.h>

void bar(double x){
[INDENT]printf("%d\n", (int)(x*25));[/INDENT]
}

int main()
{
[INDENT]bar(-5.56);[/INDENT]
[INDENT]printf("%d\n", (int)((-5.56)*25));[/INDENT]
}


[/FONT]

It should print the number -139 twice. Indeed, this is the case on a OpenSuse 10.1 *at 64 bits*. On the contrary, on a Feisty Fawn Ubuntu 7.04 *at 32 bits*, the first printf displays -138. This is also the case for other 32-bit (non-Ubuntu) machines I could try. Moerover, if I compile with g++ -O3 the result is indeed a double -139, while with -O2 it is still -138 and then -139. Any idea on why this happens? 

Thank you,

codatore

P.S.: The 64-bit compiler version is 4.3.1, the Ubuntu version is smaller

---

### Post by Soybean on 2007-07-18
I don't know exactly why it happens, though it's presumably in that mystical realm called "floating point error." My personal coping mechanism for this sort of thing is to be very explicit when I want a particular behaviour. Using ceiling or floor functions, for example. I find it easiest to assume that, unless I specifically say otherwise, floating point values are going to act in wildly unpredictable ways.

I'm sure someone knows the implementation details well enough to tell you exactly what's going on there... I just find my way easier and less error-prone. :)

---

### Post by hod139 on 2007-07-18
As Soybean said, the result of the computation is probably (print the double to confirm) -138.99999999999999999999999... and the cast operator is performing a floor operation, not a round, and you get -138 as an answer.  As stated, you should round the final answer to an int, not cast.

---

