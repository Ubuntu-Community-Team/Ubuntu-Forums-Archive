---
title: "code not working properly"
date: 2010-10-23
forum: Programming Talk
---

### Post by c2tarun on 2010-10-23
i was trying to run the following program

```

#include<stdio.h>

int main(void)
{
  char* str;
  size_t n;
  int i,count;
  n=100;
  scanf("%d",&count);
  for(i=0;i<count;i++)
    {
      getline(&str,&n,stdin);
      printf("%s\n",str);
    }
}

```it was not running as i expected.
what i expected is that it accepts a number and then accepts that number of strings and print them.
but it is accepting one less string plus printing a large gap between the number input and first string input.???
why so??

---

### Post by GeneralZod on 2010-10-23
Woo  - [deja vu](http://ubuntuforums.org/showthread.php?t=1603702&page=2)!

---

### Post by Elfy on 2010-10-23
Please do not post duplicates.

Closed.

---

