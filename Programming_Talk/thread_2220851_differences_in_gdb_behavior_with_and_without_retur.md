---
title: "differences in gdb behavior with and without return from a recursive function"
date: 2014-04-29
forum: Programming Talk
---

### Post by IAMTubby on 2014-04-29
Hello,
Consider the code below for the 3 different **return statements** mentioned in function fun.
```
#include <stdio.h>

int main(void)
{
 int ret = fun(0);
 printf("ret == [%d]\n",ret);


 return 0;
}


int fun(int house)
{
 if(house == 100)
  return 5;


 fun(house+1);
**//return 4; [COLOR=#0000ff]//output printed in the main function is ret==4[/COLOR] [COLOR=#008000]//lets' call this CASE-A[/COLOR]**
**//return; **[COLOR=#0000ff]**//output printed in the main function is ret==5 **[/COLOR][COLOR=#008000]**//lets' call this CASE-B**[/COLOR]
**//empty line without any return **[COLOR=#0000ff]**//output printed in the main function is ret==5 **[/COLOR][COLOR=#008000]**//lets' call this CASE-C**[/COLOR]
}

```

**_I have the following questions._**
1. I understand the output in case of CASE-A, but in CASE-B and CASE-C, I do not understand how 5 is printed.
As per my understanding, in CASE-B and CASE-C, the value 5 is returned only from the 100th invocation of the recursive function fun to the 99th invocation.
However, the ret value printed in main is dependent on what the first invocation of the function fun passes back to main, and this is not 5

2. I also do not understand why gdb behaves differently for CASE-A, CASE-B and CASE-C.
In CASE-A, after the **house** count goes from 0 to 100, you can see the house count going back from 100 to 0, as the highlighted line in gdb toggles between return 4; and the final closing bracket of the function fun. This makes sense since the functions are getting return'ed to their caller which is the previous invocation of the recursive function
In CASE-B and CASE-C, once the house count goes from 0-100, the next thing you see is that gdb highlights the line which called the recursive function fun inside main. **Why aren't the recursive functions being return'ed** to their caller. I would have expected the following : Once the house count goes from 0-100, it goes back from 100-0 as the highlighted line in gdb toggles between the various closing braces(I mean for each invocation of the recursive function)


**gdb traces in case my question above was not clear**
_gdb trace for CASE-A_
```

fun (house=0) at test.c:13
fun (house=1) at test.c:13
fun (house=2) at test.c:13
fun (house=3) at test.c:13
..
..
fun (house=97) at test.c:13
fun (house=98) at test.c:13
fun (house=99) at test.c:13
fun (house=100) at test.c:13
fun (house=99) at test.c:17
fun (house=98) at test.c:17
fun (house=97) at test.c:17
..
..
fun (house=3) at test.c:17
fun (house=2) at test.c:17
fun (house=1) at test.c:17
fun (house=0) at test.c:17
main () at test.c:6
```


_gdb trace for CASE-B and CASE-C_
```

fun (house=0) at test.c:13
fun (house=1) at test.c:13
fun (house=2) at test.c:13
fun (house=3) at test.c:13
..
..
fun (house=98) at test.c:13
fun (house=99) at test.c:13
fun (house=100) at test.c:13
main () at test.c:6

```

Please advise.
Thanks

PS : To see the gdb output, I use
```
gcc -g test.c
gdb -tui a.out
```

---

