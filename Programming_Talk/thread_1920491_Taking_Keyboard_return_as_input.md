---
title: "Taking Keyboard return as input"
date: 2012-02-04
forum: Programming Talk
---

### Post by c2tarun on 2012-02-04
Hi friends
I tried following code in gcc compiler.

```

#include <stdio.h>

int main()
{
        char a;
        int i = 0;
        while(i<10){
                a=getchar();
                printf("%c,%d\n",a,(int)a);
        }
}

```

I am getting following as output
[HTML]
$ ./checkgetchar < getcharInput 
T,84
a,97
r,114
u,117
n,110
K,75
u,117
m,109

,10
a,97
[/HTML]

The content of input file getcharInput is 

TarunKum
ar123

Can anyone please explain me why is it taking two inputs after m and why am I not getting the ASCII code of return. :(

---

### Post by c2tarun on 2012-02-04
I just understood it :)
I think it is printing the return and that is why there is a line change and it is not two inputs. Please correct me if i am wrong.

---

### Post by Arndt on 2012-02-05
> **c2tarun said:**
> I just understood it :)
I think it is printing the return and that is why there is a line change and it is not two inputs. Please correct me if i am wrong.

You found the answer. But you were correct that you're not getting the ASCII code 13 for return, but 10 for linefeed. That's because the terminal driver (and/or terminal emulator) translates the return key that you press into linefeed, since linefeed is the standard end-of-line character in Unix.

---

