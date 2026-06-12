---
title: "output rand() in array"
date: 2010-09-17
forum: Programming Talk
---

### Post by jon zendatta on 2010-09-17
hi. i want to output six unique integers, but only get one. 

```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main(void)
{
   int a, n;
   char m[6];
   char num[6] = {0};
   srand((unsigned)time (NULL));
   for(a = 0;a < 6;a++)
   num[a] = rand() % 40 + 1;{
   for(n = a + 1;n < 6; n++)
      m[n];
      {
       if(num[a] != m[n])
       printf("%d\n", num[a]);
       }
     }

   return 0;
}
```

---

### Post by Some Penguin on 2010-09-17
The compiler won't read your mind to figure out that you've misplaced not one but two sets of braces.

```

for (a;b;c) d;
{
  blah
}

```

is NOT the same thing as

```

for(a;b;c) {
  d;
  blah;
}

```

---

### Post by jon zendatta on 2010-09-17
thanks Some Penguin, sometimes i can't see the wood for the trees
```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main()
{
   int a, n;
   char m[6];
   char num[6] = {0};
   srand((unsigned)time (NULL));
   for(a = 0;a < 6;a++){
   num[a] = rand() % 40 + 1;
   
   for(n = a + 1;n < 6; n++){
      m[n];
       }
       if(num[a] != m[n])
       printf("%d\n", num[a]);
       }
       
     

   return 0;
}
```

---

