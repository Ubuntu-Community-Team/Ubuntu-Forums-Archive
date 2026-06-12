---
title: "_help_ on _gcc_"
date: 2007-12-13
forum: Programming Talk
---

### Post by bobotlwane on 2007-12-13
hey guys im having a problem with GCC please help
the compiler never goes to the bottom of the code, look at the code
it gives a fault, how can i solve this


>boikhutso@morobana:~$cat >ck.c<<p
> #include<stdio.h>
> int main(void)
> {
> int b;
> printf("please enter number:\n");
> scanf("%d,&b");
> printf("boikhutso %d",b);
> return 0;
> }
> p
boikhutso@morobana:~$ gcc ck.c -o ck
boikhutso@morobana:~$ ./ck
please enter number:
12
Segmentation fault (core dumped)

---

### Post by geirha on 2007-12-13
> **bobotlwane said:**
> 
> scanf("%d,&b");

try moving that last quote character a little bit further left. The way it is now, you're not storing the value you read anywhere (not anywhere legal at least)

---

### Post by samjh on 2007-12-13
Should be:
```
scanf("%d", &b);
```

---

