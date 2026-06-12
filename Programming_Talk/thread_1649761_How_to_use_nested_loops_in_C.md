---
title: "How to use nested loops in C ?"
date: 2010-12-20
forum: Programming Talk
---

### Post by binarylife on 2010-12-20
Hi 
I am trying to output the following 

1
22
333
4444
55555


...................
I've done this so far , and i don't know how to continue .


```
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int i,j;

    for (i=1;i<6;i++)
  {

         for(j=1;j<i;j++)
         printf("%d\n",j);

  }

    return 0;
}

```
any help please?

---

### Post by trent.josephsen on 2010-12-20
How many times will the outer loop run?

---

### Post by Queue29 on 2010-12-20
How many times will the inner loop run?

---

### Post by binarylife on 2010-12-20
I know outer loop must be i<6, but inner I don't know.
I need the output just to be like this :
1
22
333
4444
55555
........ 
and now I edited the code.
it gives me this output

2
3
3
4
4
4
5
5
5
5

---

### Post by Arndt on 2010-12-20
> **binarylife said:**
> I know outer loop must be i<6, but inner I don't know.
I need the output just to be like this :
1
22
333
4444
55555
........ 
and now I edited the code.
it gives me this output

2
3
3
4
4
4
5
5
5
5

Obviously you emit newlines too often. Add a test to only emit newlines when appropriate. After that, you seem to be almost there; there is just some +1 and -1 here and there.

---

### Post by dwhitney67 on 2010-12-20
Some other hints...

Think of the outer loop as a counter; that is, the number of lines of data that you want to emit.  Typically in C, a counter goes from 0 to less than N.

As for your inner loop, this will be used exclusively for the output you want to generate.  If you proceed with the same notion of utilizing a counter, then you will want to go from 0 to less than some value, which in your case, is relative to your outer loop's counter.  And as Arndt suggested, you may need to consider adding 1 to your value(s) as necessary.

---

### Post by binarylife on 2010-12-21
Thanks all 

this is the final solution :
[```



#include <stdio.h>
#include <stdlib.h>

int main()
{
    int i,j;

    for (i=1;i<6;i++)
  {


         for(j=0;j<i;j++){
         printf("%d",i);
         }
          printf("\n");
}


    return 0;
}



```

---

### Post by Arndt on 2010-12-21
> **binarylife said:**
> Thanks all 

this is the final solution :
[```



#include <stdio.h>
#include <stdlib.h>

int main()
{
    int i,j;

    for (i=1;i<6;i++)
  {


         for(j=0;j<i;j++){
         printf("%d",i);
         }
          printf("\n");
}


    return 0;
}



```

All you need now is indenting your code reasonably.

---

### Post by KdotJ on 2010-12-21
> **Arndt said:**
> All you need now is indenting your code reasonably.

+1
I really do believe that good indentation and consistent style does help a person learn programming easier.

---

### Post by r-senior on 2010-12-21
+2 ... It's no more difficult than sloppy layout. A good habit that pays off in the long run.

Part of it could just be the old tab/space chestnut of course.

---

