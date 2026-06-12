---
title: "Need Help - Error while compiling a simple C program"
date: 2013-06-08
forum: Programming Talk
---

### Post by n3t4l on 2013-06-08
Lately i have been planning to brush up my C programming skills. I realized its been rusted heavily since i have been unable to figure out that issue with this program.

```
#include <stdio.h>

#define IN_WORD 1;
#define NOT_IN_WORD 0;

int main (int argc, const char * argv[])
{
int input=0;
int count=0;
int flag=NOT_IN_WORD;

while ((input=getchar()) != EOF)
{
if ((flag == NOT_IN_WORD) && (input != ' ' || input != '\t' || input != '\n'))
{
flag=IN_WORD;
count++;
}
}

printf("No of work in input file = %d\n", count);
return 0;
}
```

And when i compile this code i get the below error:
```
$ gcc -o ~/bin/my_wc3 my_wc3.c
my_wc3.c: In function 'main':
my_wc3.c:14: error: expected ')' before ';' token
```

I am simply unable to figure out where i missed a ')' or some other special character.

---

### Post by xb12x on 2013-06-08
```
Remove the semicolons from your macros

#define IN_WORD 1
#define NOT_IN_WORD 0
```

---

### Post by n3t4l on 2013-06-08
thanks a lot for correcting my syntax error... it works now

---

### Post by r-senior on 2013-06-09
It's a good habit to compile with warnings turned on too:

```
$ gcc -o test -Wall -Wextra test.c
test.c: In function &#8216;main&#8217;:
test.c:6:14: warning: unused parameter &#8216;argc&#8217; [-Wunused-parameter]
test.c:6:32: warning: unused parameter &#8216;argv&#8217; [-Wunused-parameter]
```

In this case you can ignore the warnings, but other times they may be useful.

---

