---
title: "c++ array question"
date: 2009-12-14
forum: Programming Talk
---

### Post by nipunreddevil on 2009-12-14
I just tried giving this statement in my code and it allowed 10 chars
	char*s =new char[5];

Although its size should be 5.Why does it hapen

---

### Post by shailendra on 2009-12-14
Did you try reading back the 10 characters? See if you are getting exactly the same characters.

Sometimes, the compiler does not give any error when you try to write more than allocated data. In such a case your program is successfully able to write to the location which is not assigned to it. But the data in these locations get overwritten by new instruction which use the same location.

---

### Post by nipunreddevil on 2009-12-14
```
#include <iostream>
#include <string>
using namespace std;
int main(int argc, char** argv)
{
	char*s =new char[5];
	for(int i=0;i<20;i++)
	s[i]='a';
	int ctr=0;
	while(s[ctr]!='\0')
		{
		ctr++;
	}
	cout<<ctr;
	
	return 0;
}
```

Now this code is producing output as 20
why's that

---

### Post by Habbit on 2009-12-14
First of all, you are wrong in thinking it "should not work". C++ (like C) is built for speed, and so it tries not to impose any overhead you might not want. In particular, why should the compiler insert code to check each array access if _your_ logic already makes sure not to overrun its bounds? Thus, addressing an element past the last in an array is *undefined behavior*. In C-speak, it means that anything could happen, from nothing (i.e. it "works"), to crashing horribly and immediately, to corrupting the state of the program in strange ways so that it might, or might not crash hours later in an unrelated function (a "heisenbug").

C (and C++) arrays are just the thinnest possible wrapper over the system memory, and the only checking performed on them is static type safety. Other than that, you can overrun them and the compiler will not complain. In your case, it does not even _know_ the length of the array (because it is a dynamically-allocated array), but most wouldn't say a word if you had declared it with a compiler-known length such as "char[5] s". If you want bounds checking, use std::vector<T> and access your elements using the "at" method (the vector subscript operator [] has no bounds checking, just like an array... remember: no unnecessary overhead).

---

### Post by shailendra on 2009-12-14
This is due to the buffer overflow. Try using the following statement:

for(int i=0;i<5;i++)

or

char*s =new char[20]

---

### Post by jollysnowman on 2009-12-14
There is no boundary checking in C/C++.

---

### Post by mwiseman on 2009-12-14
> **nipunreddevil said:**
> ```
#include <iostream>
#include <string>
using namespace std;
int main(int argc, char** argv)
{
    char*s =new char[5];
    for(int i=0;i<20;i++)
    s[i]='a';
    int ctr=0;
    while(s[ctr]!='\0')
        {
        ctr++;
    }
    cout<<ctr;
    
    return 0;
}
```Now this code is producing output as 20
why's that Your code invokes undefined behaviour. That's why.

---

### Post by Alex Libman on 2009-12-14
First thing's first - your opening curly braces are in all the wrong places.  :tongue:

Oh, and the buffer overflow, but that might have been an intentional fashion statement.

---

