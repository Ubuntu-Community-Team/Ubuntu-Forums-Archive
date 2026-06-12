---
title: "help"
date: 2009-05-07
forum: Programming Talk
---

### Post by book_life on 2009-05-07
hi fellas i am learning C! 
pls help me with this question i have expected the output of this program to be
[B]10
-1[/B] 
but it was like what i have expected but it was
[B]10
0[/B]
how can it be please help me?

#include<stdio.h>
int main()
{
 int i, k=8;
i=k++-k++;
printf("%d\n",k);
printf("%d\n",i);
return 0;
}

---

### Post by Temposs on 2009-05-07
Since you have put the ++ after the variable, it is not executed until the rest of the line is executed. So, for the line:

```
i=k++-k++
```

This is equivalent to:

```
i=k-k;
k++;
k++;
```

If you want to get -1 as a result for i, you must change the line to:

```
i=k++-++k;
```

---

