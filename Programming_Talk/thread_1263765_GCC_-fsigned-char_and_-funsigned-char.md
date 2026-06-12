---
title: "GCC -fsigned-char and -funsigned-char"
date: 2009-09-11
forum: Programming Talk
---

### Post by kashyap_ankur on 2009-09-11
Hello All,

I have a question, or I should rather say, a doubt. Consider the following piece of code, sample.c:

```
#include <stdio.h>

void some_func (char *arg) {}

int main ()
{
    signed char *p;

    some_func (p);

    return 0;
}
```Case 1:
When compiled using ---> **gcc -Wall -o sample sample.c**
[COLOR=Red]sample.c: In function ‘main’:
sample.c:9: warning: pointer targets in passing argument 1 of ‘some_func’ differ in signedness[/COLOR]

Case 2:
When compiled using ---> **gcc -Wall -fsigned-char -o sample sample.c**
[COLOR=Red]sample.c: In function ‘main’:
sample.c:9: warning: pointer targets in passing argument 1 of ‘some_func’ differ in signedness[/COLOR]

I understand that in the first case the warning is there because instead of char* a signed char* is passed to some_func. But in the second case, when -fsigned-char is used --- shouldn't it tell GCC to treat the signature of **some_func **as void **some_func (signed char *arg);**

Please let me know your thoughts in this regard.

With Regards,
Ankur

---

### Post by MadCow108 on 2009-09-11
the switch only changes how gcc interprets the char
it still warns you that gcc has to make an interpretation of the char no matter if you tell it how to interpret it

the purpose of the warning is that you fix your code so that the result is guaranteed to be the same on any plattform without the switch

---

### Post by kashyap_ankur on 2009-09-11
> **MadCow108 said:**
> the switch only changes how gcc interprets the char
it still warns you that gcc has to make an interpretation of the char no matter if you tell it how to interpret it

the purpose of the warning is that you fix your code so that the result is guaranteed to be the same on any plattform without the switch
Thank you very much.

---

