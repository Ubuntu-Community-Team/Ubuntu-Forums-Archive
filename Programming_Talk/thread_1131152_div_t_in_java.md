---
title: "div_t in java"
date: 2009-04-20
forum: Programming Talk
---

### Post by abraxas334 on 2009-04-20
Hello,
trying to tranlsate a ++ program into Java. I came across this line and i was wondering there is something similar like div_t in java.

[PHP]

#include <stdio.h>
#include <stdlib.h>

int main ()
{
  div_t divresult;
  
  divresult = div (28, 5);
  
  printf ("28 / 5 = %d ( %d", divresult.quot, divresult.rem);
  return 0;
}



[/PHP]
thanks

---

### Post by jespdj on 2009-04-20
There's nothing built-in in Java that is more or less the same as [div_t](http://www.cplusplus.com/reference/clibrary/cstdlib/div_t/). In C++, it's just a structure with two members, quot and rem. You could easily write something like that yourself in Java:
```
public class DivT
{
    private int quot;
    private int rem;

    public int getQuot() {
        return quot;
    }

    public void setQuot(int quot) {
        this.quot = quot;
    }

    public int getRem() {
        return rem;
    }

    public void setRem(int rem) {
        this.rem = rem;
    }
}
```
Java has integer division / and remainder % operators that you can use to get the result of an integer division and the remainder.

---

### Post by abraxas334 on 2009-04-27
Thanks :) Guess that works well :)

---

