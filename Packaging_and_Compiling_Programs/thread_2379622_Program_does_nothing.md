---
title: "Program does nothing"
date: 2017-12-07
forum: Packaging and Compiling Programs
---

### Post by raleigh3 on 2017-12-07
When I run this, nothing happens.

```
/* gcc numbers.c -o numbers  */
#include <stdio.h>
 
void print(int);
 
int main()
{
  int n;
 
  scanf("%d", &n);
 
  print(n);
 
  return 0;
}
 
void print(int n)
{
  static int c = 1;
 
  if (c == n+1)
    return;
 
  printf("%d\n", c);
  c++;
  print(n);
}
```

---

### Post by steeldriver on 2017-12-07
How exactly are you running it? are you giving `scanf` any input to scan?

---

### Post by raleigh3 on 2017-12-07
./numbers

Prog is supposed to print numbers.

---

### Post by steeldriver on 2017-12-07
It only prints numbers after you give it an initial number `n`

```

$ ./numbers
4 <ENTER>
1
2
3
4

```

or 
```

$ echo 4 | ./numbers
1
2
3
4

```

Otherwise, it will just sit at

```

  scanf("%d", &n);

```

waiting for input

---

### Post by raleigh3 on 2017-12-07
Thanks. I am looking for a C  programming forum.

---

### Post by faraco2 on 2017-12-19
> **raleigh3 said:**
> Thanks. I am looking for a C  programming forum.


You may want to visit [cprogramming]("https://cboard.cprogramming.com/c-programming/") forum for advanced C programming topics in the future. ;)

---

