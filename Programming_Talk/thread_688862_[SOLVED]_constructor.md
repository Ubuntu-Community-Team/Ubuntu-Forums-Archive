---
title: "[SOLVED] constructor?"
date: 2008-02-05
forum: Programming Talk
---

### Post by chris200x9 on 2008-02-05
I have a problem I can't get this to compile 

```
 
 
#include <iostream>
#include <cmath>
using namespace std;
void printNumber (float num, float base);
cout << log10(num) / log10(base);
 
 
 
int main()
{
	float num;
	float base;
cout << "what number do you want?" << endl;
cin >> num;
cout << "what base do you want?";
cin >> base;
printNumber(num, base);

return 0;
}


```


it gives me an error that says expected concstructor destructor or type conversion.

edit: sorry in advance I'm a super n00b and I haven't used functions in a long while

---

### Post by yabbadabbadont on 2008-02-05
Instead of ```
void printNumber (float num, float base);
cout << log10(num) / log10(base);

```
try
```
void printNumber (float num, float base) {
cout << log10(num) / log10(base);
}

```

---

### Post by chris200x9 on 2008-02-05
yep thanx :)

---

