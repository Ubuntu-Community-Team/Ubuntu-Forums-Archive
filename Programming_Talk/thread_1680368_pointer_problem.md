---
title: "pointer problem"
date: 2011-02-02
forum: Programming Talk
---

### Post by el_diablo on 2011-02-02
[SIZE=4]#include<stdio.h>
int main()
{
int a[]={10,20,30,40,50};
int j;
for(j=0;j<5;j++)
{
printf("%d\n",*a);
a++;
}
return 0;
}

hi..
when i run this program in gcc,"Lvalue require"error comes.i am not able to understand this behavior of pointer.
Please help 
[/SIZE]

---

### Post by unknownPoster on 2011-02-02
Perhaps this is an exercise in pointers, but if it is not, the following code achieves what I assume to be your desired result.

```

 #include<stdio.h>
int main(){
   int a[]={10,20,30,40,50};
   int j;
       for(j=0;j<5;j++){
          printf("%d\n",a[j]);
       }
return 0;
}

```

---

### Post by SevenMachines on 2011-02-02
You can't modify the address of an array as in
```
[SIZE=4]int a[]={10,20,30,40,50};
[/SIZE]a++; 
```However, you can alter a pointer to it as in,
```
[SIZE=4]int a[]={10,20,30,40,50};
[/SIZE]int * p = &a[0];
p++;
```

---

### Post by Arndt on 2011-02-02
> **el_diablo said:**
> [SIZE=4]#include<stdio.h>
int main()
{
int a[]={10,20,30,40,50};
int j;
for(j=0;j<5;j++)
{
printf("%d\n",*a);
a++;
}
return 0;
}

hi..
when i run this program in gcc,"Lvalue require"error comes.i am not able to understand this behavior of pointer.
Please help 
[/SIZE]

We had a lengthy discussion recently on what was an almost identical program and the same error: [http://ubuntuforums.org/showthread.php?t=1676330](http://ubuntuforums.org/showthread.php?t=1676330).

---

### Post by rnerwein on 2011-02-03
> **Arndt said:**
> We had a lengthy discussion recently on what was an almost identical program and the same error: [http://ubuntuforums.org/showthread.php?t=1676330](http://ubuntuforums.org/showthread.php?t=1676330).

hi
the reason is that an array is a "static" address with that you can't change with ++.
a pointer is a variable address.
thats in assembler: ( sorry i know only full assembler but i think it works the same way )
---> on an array the call is only: la ( load address ) and you can reference the storage.
---> whit pointer the system have to call: la ( the address of the pointer )and then ld (load) and then you can reference the storage.

pointers are flexible ( often to use ) but when you really know what sizes you want --> arrays are faster.
ciao

---

### Post by trent.josephsen on 2011-02-03
> **rnerwein said:**
> hi
the reason is that an array is a "static" address with that you can't change with ++.
a pointer is a variable address.
thats in assembler: ( sorry i know only full assembler but i think it works the same way )
---> on an array the call is only: la ( load address ) and you can reference the storage.
---> whit pointer the system have to call: la ( the address of the pointer )and then ld (load) and then you can reference the storage.

pointers are flexible ( often to use ) but when you really know what sizes you want --> arrays are faster.
ciao
This doesn't really make sense.

---

### Post by forrestcupp on 2011-02-04
Create a pointer to **a** and increment that pointer instead of trying to increment **a**. You can't change a's starting memory location, but you can change the value of a pointer that references a's starting memory location.

```
int a[] = {10,20,30,40,50};
int *b = a;

...

printf("%d\n",*b);
b++;
```

I hope we're not doing your homework for you.

---

