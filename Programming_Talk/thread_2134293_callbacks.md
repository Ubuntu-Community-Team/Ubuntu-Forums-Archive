---
title: "callbacks"
date: 2013-04-10
forum: Programming Talk
---

### Post by mycy on 2013-04-10
Hello everyone i am trying to understand how callbacks in c work but i am little confused. How can there be a function call without sending any parameters at all? what values are used as parameters for that function? For example if i have the code below how the result of the function is gonna be calculated?

```
int function (int param1, int param2){
.
.
}

int main()
{
function_call=function;

}

```
thank u

---

### Post by dwhitney67 on 2013-04-11
In your main() function, that is not a function call.  That is merely an assignment.

Here's a complete example:
```

#include <stdio.h>

void function(int val1, int val2)
{
    printf("val1 = %d, val2 = %d\n", val1, val2);
}

int main()
{
    void (*function_call)(int, int);

    function_call = function;    // assignment

    function_call(10, 20);    // call function

    return 0;
}

```
Alternatively, this statement is legal too:
```

...
    void (*function_call)(int, int) = function;
...

```

---

### Post by mycy on 2013-04-11
ok thank u  but in your example what if i had an assignment to a struct and the only other place where the struct is used is as a parameter in an other function. For example:

void fun(.....)
{
  ...
  fun_1(..., &struct_callbacks);
  .....
}

int function (int a,int b){
..  

}

int main(){
struct strc_call struct_callbacks = {function};
..
}

---

### Post by dwhitney67 on 2013-04-11
> **mycy said:**
> ok thank u  but in your example what if i had an assignment to a struct and the only other place where the struct is used is as a parameter in an other function. For example:


Please post the code you are attempting to compile, not just snips of theoretical code.  I'm not in the habit of developing s/w for free.

---

