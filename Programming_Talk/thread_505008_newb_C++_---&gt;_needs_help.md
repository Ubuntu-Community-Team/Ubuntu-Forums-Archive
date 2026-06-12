---
title: "newb C++ ---&gt; needs help"
date: 2007-07-19
forum: Programming Talk
---

### Post by M!K3_$ on 2007-07-19
hello. i just started learning C++ yesterday
looks good so far
i am going through SAMS teach yourself C++ in 21 days
i am stuck on listing 2.4  (if u have the book)

```
// Listing 2.3 - using namespace std
#include <iostream>
int main()
{
	using namespace std;
	
	cout << "Hello just a test to see if this works\n";
	cout << "Hopefully it works" << endl;
}

```

unfortunately, when i tried to compile i got this error

```
g++: 2.4-using namespace: linker input file unused because linking not done
``` 

what did i do wrong

thanks
mike

---

### Post by yabbadabbadont on 2007-07-19
I just cut and pasted your code into go.cpp, then ran "g++ go.cpp" and it compiled without error or warnings to a.out as it should.  (It produced the proper output too).  How did you compile it?

---

### Post by M!K3_$ on 2007-07-19
i wrote and compiled using the geany IDE
but ill try it through terminal

---

### Post by M!K3_$ on 2007-07-19
i realize wat i did wrong now
didnt save it as .cpp
wow...
who feels like a moron

thanks anyways yabbadabadont

---

