---
title: "parameter return value"
date: 2007-12-22
forum: Programming Talk
---

### Post by metricben on 2007-12-22
I am trying to set up a function that takes (as a parameter) a pointer to a variable, then can change this value in C++.  Following is a short example:

```
int n = 2;

changevalue(&n);

changevalue(&num){
    *num = 4;
}
cout << n; //should be "4"

```

Can someone explain to me how this would work?  Im sure I ahve seen it done someplace...

Basically this is a way of passing to a fuction a variable that can be changed from within the function.

Thanks,
Ben

---

### Post by geirha on 2007-12-22
You should read up on the address-of operator. Wikibooks explains it fairly well [http://en.wikibooks.org/wiki/C%2B%2B_Programming/Operators#address-of_operator_.22.26.22](http://en.wikibooks.org/wiki/C%2B%2B_Programming/Operators#address-of_operator_.22.26.22)

Here's an example of what seems to be what you wanted to do:
```
#include <iostream>

void changevalue(int& num)
{
    num= 4;
}

int main()
{
    int n= 2;
    changevalue(n);
    std::cout << n << std::endl;
    return 0;
}

```

---

### Post by engla on 2007-12-22
> **metricben said:**
> 
```
changevalue(&num){

```
This line should be
```
void changevalue(int *num){

```you want to take a pointer to int as parameter

> **geirha said:**
> You should read up on the address-of operator. Wikibooks explains it fairly well [http://en.wikibooks.org/wiki/C%2B%2B_Programming/Operators#address-of_operator_.22.26.22](http://en.wikibooks.org/wiki/C%2B%2B_Programming/Operators#address-of_operator_.22.26.22)

Here's an example of what seems to be what you wanted to do:
```
#include <iostream>

void changevalue(int& num)
{
    num= 4;
}

int main()
{
    int n= 2;
    changevalue(n);
    std::cout << n << std::endl;
    return 0;
}

```
We are mixing two concepts here. First, there is pointer and addresses which is a common C and C++ concept. What you are using here is the pure C++ concept *Reference variables* however; in C you can use "&variable" to get the address of a varaible, in C++ you can _declrare_ a reference as "int &var = othervar"

---

### Post by metricben on 2007-12-22
Thanks alot!

Geirha your solution worked.  I should probably learn a bit more about pointers.etc.


ben

---

### Post by metricben on 2007-12-22
Another question:

How would I do this but pass a pointer to the function, so I could have dynamic memory?

Thanks

---

### Post by geirha on 2007-12-22
you mean like this?
```
#include <iostream>

void changevalue(int* num)
{
    *num= 4;
}

int main()
{
    int *p= new int (2);
    std::cout << *p << std::endl;
    changevalue(p);
    std::cout << *p << std::endl;
    delete p;
    return 0;
}

```

---

### Post by metricben on 2007-12-22
exactly what I wanted thanks

---

