---
title: "please help opening files in C"
date: 2007-10-19
forum: Programming Talk
---

### Post by podiyan on 2007-10-19
I have to open many small files in C. But the files are in the form a.001, a.002, .....a.00n.
I lke to open files in a loop.
like when int n = 1 open a.001 
upto n=n open a.00n.

Can you please help me. How to do it in normal way.

I had an idea like this but its not working, what went wrong

#include <stdio.h>
#include <stdlib.h>
int main()
{
int n =1 ;
char name[64];
for(int k=1; k==n; k++)
{
sscanf(name,"a.%03d", &n);
int f=open(name,O_RDONLY);
close(f);
}
}

---

### Post by Wybiral on 2007-10-19
```

FILE *f = fopen(name, "r");
fclose(f);

```

---

### Post by podiyan on 2007-10-19
But please tell me how i can open assaign values a.001, a.002, ... in loops to variable name
am new to C

---

### Post by dwhitney67 on 2007-10-19
try snprintf().

for info run this command:

[FONT="Courier New"]$ man snprintf()[/FONT]

---

### Post by podiyan on 2007-10-19
i solved it using sprintf

Thx for ur helps

---

