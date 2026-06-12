---
title: "reference parameter in c"
date: 2013-05-13
forum: Programming Talk
---

### Post by ferizhandi on 2013-05-13
how to pass a reference parameter to function?!?
i tested this code: 
```
void func ( int * var)
{
      int x=3;
      var =x;
}
int main()
{
     int a=4;
     func( & a);
     printf("%d",a);
     return 0;
}
```

output isn't 3.

---

### Post by r-senior on 2013-05-13
```
void func ( int * var)
{
    int x=3;
    [COLOR="#FF0000"]var =x[/COLOR];
}
```

The parameter is a pointer to the value you want to change, but you are assigning a value to the pointer itself, instead of to the value that the pointer points to.

---

### Post by ferizhandi on 2013-05-13
yeah, but i test this instruction:
*var =x;
but not correct.

---

### Post by marianoa on 2013-05-13
This works ok for me 
```
#include <stdio.h>
 
void func ( int *var){
  int x = 3;
  *var = x;
}

int main(){
  int a=4;
  func(&a);
  printf("%d\n",a);
  return 0;
}

```

I get 3

---

### Post by ferizhandi on 2013-05-13
i am runing this code, but when  arrive to this instruction ( *var = x; ) , program stop and say this:
Segmentation fault (core dumped)

---

### Post by marianoa on 2013-05-13
It's strange, I've just pasted the code I posted before in a file, saved and compiled it with 

```
cc file_name.c -o executable_name
```

and it works. The gcc version installed on my pc is 4.7.3

---

