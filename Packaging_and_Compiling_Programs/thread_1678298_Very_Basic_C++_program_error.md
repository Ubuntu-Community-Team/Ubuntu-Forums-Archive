---
title: "Very Basic C++ program error"
date: 2011-01-30
forum: Packaging and Compiling Programs
---

### Post by nizghat on 2011-01-30
Hi guyz,
I m shocked getting an error in my .cpp file
U know what it is ?
I wrote a function with Name Display() and now m calling it inside the main. when i compile it with g++ it gives and error
```
#include<iostream>

using namespace std;

int main()
{	
	Display();
	return 0;
}

//Some Global Functions Defined
void Display()
{
	cout<<"Display Function Called"<<endl;
}
```
this is the error

```
main.cpp: In function ‘int main()’:
main.cpp:10: error: ‘Display’ was not declared in this scope
```


I dont know what is the problem, any one check it and tell me what it really mean

---

### Post by Rab22 on 2011-01-30
You need to put the function above it, or use a function header to signify that the function definition will come later.

---

### Post by Rab22 on 2011-01-30
Here, this webpage will provide you some additional details on functions.

[http://www.cplusplus.com/doc/tutorial/functions2/](http://www.cplusplus.com/doc/tutorial/functions2/)

---

### Post by nizghat on 2011-01-30
Ok i did this and its now working fine
```

void Display()
```

thankx

---

