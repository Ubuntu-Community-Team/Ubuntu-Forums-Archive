---
title: "C character scanf"
date: 2012-06-03
forum: Programming Talk
---

### Post by shashanksingh on 2012-06-03
```

#include<stdio.h>

int main()
{
    int i;
    char k[10];

    for(i=0;i<2;i++)
    {       
        scanf("%c",&k[i]);
        printf("%c",k[i]);      
    }

    return 0;
}
```
When I execute the above code, why does it not take input twice? It just prints it once and exits. It somehow takes "return" as the second input I believe

---

### Post by dwhitney67 on 2012-06-03
Twice, huh?

How many keys on your keyboard did you press?  Think carefully.


P.S.  Your conclusion is correct.

---

