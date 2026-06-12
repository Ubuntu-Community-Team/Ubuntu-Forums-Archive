---
title: "problem with g++ cin"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by johnboles on 2008-08-08
I tried the following program:
cin example
/**************************************
cin example
***************************************/
#include <iostream>

int main(void)
{
using  namespace std;

int number;

cout<<"Please enter a number"<<endl;
cin >> number;
cout<<"your number is :"<<number<<endl;
return 0;
}

the g++ compiler gave me an error: 'cin' does not name a type

what am I doing wrong?

---

### Post by StOoZ on 2008-08-08
try removing the spaces...

---

### Post by Rolcol on 2008-08-08
Strange... I just compiled exactly what you pasted and everything worked for me.
```

roly@---:~/Desktop$ nano test.cpp
roly@---:~/Desktop$ g++ test.cpp 
roly@---:~/Desktop$ ./a.out 
Please enter a number
10
your number is :10
roly@---:~/Desktop$ 
```
```

roly@---:~/Desktop$ cat test.cpp 
/**************************************
cin example
***************************************/
#include <iostream>

int main(void)
{
using namespace std;

int number;

cout<<"Please enter a number"<<endl;
cin >> number;
cout<<"your number is :"<<number<<endl;
return 0;
}
roly@---:~/Desktop$ 
```

---

### Post by johnboles on 2008-08-08
I just found the problem.
I had typed the name of the program "cin example" as a first line in the file.  When the compiler hit the cin it expected a type to be named.
thanks for the quick response
John

---

