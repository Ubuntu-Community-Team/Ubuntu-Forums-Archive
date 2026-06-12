---
title: "printf vs cout gives differnet results on floats c++"
date: 2008-09-18
forum: Programming Talk
---

### Post by monkeyking on 2008-09-18
Can someone explain from this simple program
All the tabs are just for nice output format
[PHP]
#include <iostream>

int main(){
  float f = 30.3;
  
  printf("myfloatval in printf :\t\t%f\n",f);
  std::cout << "myfloatval in operator`<<` :\t" <<f <<std::endl;
}
[/PHP]

Why the output gives this
```

./a.out 
myfloatval in printf :		30.299999
myfloatval in operator`<<` :	30.3

```

I find this behavior strange.

Thanks in advance

---

### Post by Npl on 2008-09-18
you cant represent 30.3 in floats, so your variable 'f' contains a value close to it, but not exactly 30.3.

you can make << print out more digits or make printf print less to get the same results. I dont know the defaults for either.

---

### Post by dwhitney67 on 2008-09-18
I don't know the exact cause for the anomaly you are seeing, but I do know that if you replace the %f with a %g in the printf() format, then the output will look the same.

Bear in mind though that the %g is used to display either exponential notation (lower-case) or floating-point numbers, depending on the size of the number.

IMO it is best to avoid declaring floats and to rely on the more precise double data type.

Here's a link to the printf() format operators:
[http://www.cppreference.com/wiki/c/io/printf](http://www.cppreference.com/wiki/c/io/printf)

P.S.  I just tried your program; you can also try specifying %.1f to force a single digit after the decimal point.

---

### Post by monkeyking on 2008-09-18
Thanks for your replies.
It just seems strange I guess.

Does anyone know if it possible to change the default outputting format of operator "<<".

So for instance I can show more decimals ?

thanks again

---

### Post by dwhitney67 on 2008-09-18
You do know that with a little research, you probably could find the answer yourself.

[PHP]#include <iostream>
#include <iomanip>

...
float value = 33.3;

std::cout << std::setprecision(2) << std::fixed << value << std::endl;[/PHP]

---

